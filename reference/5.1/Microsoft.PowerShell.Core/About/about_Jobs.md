---
description: Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: bce65f0bd173f936e868c3bef048ecac3f4f4ca6
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524435"
---
# <a name="about-jobs"></a>Om jobb

## <a name="short-description"></a>Kort beskrivning
Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.

## <a name="long-description"></a>Lång beskrivning

PowerShell kör kommandon och skript via jobb samtidigt. Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.

- `RemoteJob` -Kommandon och skript körs på en fjärrsession. Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).
- `BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn.
- `PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn. Mer information finns i [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).

Att köra skript på distans, på en separat dator eller i en separat process, ger bra isolering. Eventuella fel som inträffar i fjärrjobbet påverkar inte andra jobb som körs eller den överordnade sessionen som startade jobbet. Dock lägger dataremoting till overhead, inklusive objekt serialisering. Alla objekt serialiseras och avserialiseras när de skickas mellan den överordnade sessionen och fjärrsessionen (Job). Serialisering av stora komplexa data objekt kan förbruka stora mängder beräknings-och minnes resurser och överföra stora mängder data i nätverket.

Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar. Om ett jobb har ett kritiskt fel som låser processen avslutas alla andra jobb i processen.

Trådbaserade jobb kräver dock mindre kostnader. De använder inte Remoting-skiktet eller serialiseringen. Resultat objekt returneras som referenser till Live-objekt i den aktuella sessionen. Utan den här omkostnaderna körs trådbaserade jobb snabbare och använder färre resurser än andra jobb typer.

> [!IMPORTANT]
> Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data. Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd. Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.

Det finns två sätt att komma runt den här situationen:

1. Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner. Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).
1. Använd `Start-Process` för att skapa en ny process i stället för ett jobb. Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).

## <a name="the-job-cmdlets"></a>Jobb-cmdletar

|Cmdlet          |Beskrivning                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |Startar ett bakgrunds jobb på en lokal dator.           |
|`Get-Job`       |Hämtar bakgrunds jobben som startades i      |
|                |aktuell session.                                       |
|`Receive-Job`   |Hämtar resultatet av bakgrunds jobb.                   |
|`Stop-Job`      |Stoppar ett bakgrunds jobb.                                |
|`Wait-Job`      |Ignorerar kommando tolken tills ett eller flera jobb|
|                |full.                                              |
|`Remove-Job`    |Tar bort ett bakgrunds jobb.                              |
|`Invoke-Command`|Parametern **AsJob** skapar ett bakgrunds jobb på en  |
|                |Fjärran sluten dator. Du kan använda `Invoke-Command` för att köra   |
|                |valfritt jobb kommando, inklusive `Start-Job` .       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>Starta ett jobb på den lokala datorn

Om du vill starta ett bakgrunds jobb på den lokala datorn använder du `Start-Job` cmdleten.

Om du vill skriva ett `Start-Job` kommando omger du kommandot som jobbet kör inom klammerparenteser ( `{}` ). Använd parametern **script block** för att ange kommandot.

Följande kommando startar ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.

```powershell
Start-Job -ScriptBlock {Get-Process}
```

När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart, även om jobbet tar en längre tid att slutföra. Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.

`Start-Job`Kommandot returnerar ett objekt som representerar jobbet. Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.

Du kan spara jobbobjektet i en variabel och sedan använda det med andra **jobb** -cmdletar för att hantera bakgrunds jobbet. Följande kommando startar ett jobb objekt och sparar det resulterande jobbobjektet i `$job` variabeln.

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

## <a name="getting-job-objects"></a>Hämtar jobb objekt

`Get-Job`Cmdleten returnerar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen. Utan parametrar `Get-Job` returnerar alla jobb som startades i den aktuella sessionen.

```powershell
Get-Job
```

Jobbobjektet innehåller jobbets tillstånd, vilket indikerar om jobbet har avslut ATS. Ett slutfört jobb har statusen **slutförd** eller **misslyckad**. Ett jobb kan också **blockeras** eller **köras**.

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

Du kan spara jobbobjektet i en variabel och använda det för att representera jobbet i ett senare kommando. Följande kommando hämtar jobbet med ID 1 och sparar det i `$job` variabeln.

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a>Hämta resultatet av ett jobb

När du kör ett bakgrunds jobb visas inte resultaten direkt. Använd cmdleten för att hämta resultatet av ett bakgrunds jobb `Receive-Job` .

I följande exempel `Receive-Job` hämtar cmdlet resultatet från jobbet med jobbobjektet i `$job` variabeln.

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

Du kan spara resultatet av ett jobb i en variabel. Följande kommando sparar resultatet av jobbet i `$job` variabeln till `$results` variabeln.

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a>Hämta och behålla del jobbs resultat

`Receive-Job`Cmdlet: en hämtar resultatet av ett bakgrunds jobb. Om jobbet har slutförts, `Receive-Job` hämtas alla jobb resultat. Om jobbet fortfarande körs `Receive-Job` hämtar de resultat som har genererats hittills. Du kan köra `Receive-Job` kommandon igen för att få återstående resultat.

Som standard `Receive-Job` tar bort resultaten från cachen där jobb resultat lagras. När du kör `Receive-Job` igen får du bara de nya resultaten som kom efter den första körningen.

Följande kommandon visar resultatet av kommandon som `Receive-Job` körs innan jobbet har slutförts.

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

Använd parametern **Keep** för att förhindra `Receive-Job` borttagning av jobb resultat som returneras. Följande kommandon visar effekterna av att använda parametern **Keep** i ett jobb som inte har slutförts än.

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a>Väntar på resultaten

Om du kör ett kommando som tar lång tid att slutföra kan du använda egenskaperna för jobbobjektet för att fastställa när jobbet har slutförts. Följande kommando använder `Get-Job` objektet för att hämta alla bakgrunds jobb i den aktuella sessionen.

```powershell
Get-Job
```

Resultaten visas i en tabell. Jobbets status visas i kolumnen **status** .

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

I det här fallet visar egenskapen **State** att jobb 2 fortfarande körs. Om du vill använda `Receive-Job` cmdleten för att hämta jobb resultaten nu skulle resultaten vara ofullständiga. Du kan använda `Receive-Job` cmdleten upprepade gånger för att hämta alla resultat. Använd egenskapen **State** för att fastställa när jobbet har slutförts.

Du kan också använda parametern **wait** i `Receive-Job` cmdleten. Vid användning av den här parametern returnerar cmdleten inte kommando tolken förrän jobbet har slutförts och alla resultat är tillgängliga.

Du kan också använda `Wait-Job` cmdleten för att vänta på ett eller alla resultat av jobbet. `Wait-Job` låter dig vänta på ett eller flera jobb eller för alla jobb.
Följande kommando använder `Wait-Job` cmdleten för att vänta på ett jobb med **ID**
10.

```powershell
Wait-Job -ID 10
```

Därför ignoreras PowerShell-prompten tills jobbet har slutförts.

Du kan också vänta en fördefinierad tids period. Det här kommandot använder **timeout** -parametern för att begränsa vänte tiden till 120 sekunder. När tiden går ut returneras kommando tolken, men jobbet fortsätter att köras i bakgrunden.

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>Stoppa ett jobb

Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten. Följande kommando startar ett jobb för att hämta varje post i system händelse loggen. Objektet sparas i `$job` variabeln.

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

Följande kommando stoppar jobbet. En pipeline-operator () används `|` för att skicka jobbet i `$job` variabeln till `Stop-Job` .

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>Ta bort ett jobb

Om du vill ta bort ett bakgrunds jobb använder du `Remove-Job` cmdleten. Följande kommando tar bort jobbet i `$job` variabeln.

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>Undersöka ett misslyckat jobb

Jobb kan inte utföras av många olika orsaker. jobbobjektet innehåller en **orsaks** egenskap som innehåller information om orsaken till felet.

I följande exempel startas ett jobb utan de autentiseringsuppgifter som krävs.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

Granska **orsaks** egenskapen för att hitta det fel som gjorde att jobbet inte kunde köras.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

I det här fallet misslyckades jobbet eftersom fjärrdatorn krävde explicita autentiseringsuppgifter för att köra kommandot. Egenskapen **orsak** innehåller följande meddelande:

> Det gick inte att ansluta till fjärrservern. följande fel meddelande visas: "åtkomst nekad".

## <a name="see-also"></a>Se även

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start – jobb](xref:Microsoft.PowerShell.Core.Start-Job)
- [Hämta jobb](xref:Microsoft.PowerShell.Core.Get-Job)
- [Mottagning – jobb](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stoppa – jobb](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Ta bort – jobb](xref:Microsoft.PowerShell.Core.Remove-Job)
- [Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)
