---
description: Förklarar hur du löser problem med schemalagda jobb
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: 924205edb9d44724cfef201d84baa304ecde67ad
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270963"
---
# <a name="about-scheduled-jobs-troubleshooting"></a>Om fel sökning av schemalagda jobb

## <a name="short-description"></a>Kort beskrivning

Förklarar hur du löser problem med schemalagda jobb

## <a name="long-description"></a>Lång beskrivning

I det här dokumentet beskrivs några av de problem som kan uppstå när du använder funktionerna för schemalagda jobb i PowerShell och det föreslår lösningar på dessa problem.

Innan du använder schemalagda PowerShell-jobb kan du läsa mer i [about_Scheduled_Jobs](about_Scheduled_Jobs.md) och relaterade schemalagda uppgifter om ämnen.

Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).

## <a name="cant-find-job-results"></a>Det går inte att hitta jobb resultaten

### <a name="basic-method-for-getting-job-results-in-powershell"></a>Grundläggande metod för att hämta jobb resultat i PowerShell

När ett schemalagt jobb körs skapas en instans av det schemalagda jobbet. Om du vill visa, hantera och hämta resultatet av schemalagda jobb instanser använder du jobb-cmdletarna.

> [!NOTE]
> Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen. Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .

Om du vill hämta en lista över alla instanser av ett schemalagt jobb använder du `Get-Job` cmdleten.

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

`Get-Job`Cmdleten skickar **ProcessJob** -objekt nedåt i pipelinen. `Format-Table`Cmdleten visar egenskaperna **Name** , **ID** och **PSBeginTime** för en schemalagd jobb instans i en tabell.

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

Använd cmdleten för att hämta resultatet av en instans av ett schemalagt jobb `Receive-Job` . Följande kommando hämtar resultatet från den senaste instansen av ProcessJob (ID = 50).

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a>Grundläggande metod för att hitta jobb resultat på disk

Om du vill hantera schemalagda jobb använder du jobb-cmdletarna, till exempel `Get-Job` och `Receive-Job` .

Om inte `Get-Job` hämtar jobb instansen eller `Receive-Job` inte hämtar jobb resultaten kan du söka igenom körnings historiken för jobbet på disk.
Körnings historiken innehåller en post för alla Utlös ande jobb instanser.

Kontrol lera att det finns en tidsstämpel-namngiven katalog i katalogen för ett schemalagt jobb på följande sökväg:

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

Ett exempel:

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

Till exempel `Get-ChildItem` hämtar cmdleten körnings historiken på disk för det schemalagda **ProcessJob** -jobbet.

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

Varje timestamp-namngiven katalog representerar en jobb instans. Resultaten för varje jobb instans sparas i en **Results.xml** -fil i katalogen timestamp-named.

Följande kommando hämtar till exempel **Results.xml** filer för varje Sparad instans av det schemalagda **ProcessJob** -jobbet. Om **Results.xml** -filen saknas kan inte PowerShell returnera eller Visa jobb resultaten.

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

Jobb-cmdleten kanske inte kan hämta schemalagda jobb instanser eller deras resultat eftersom modulen **PSScheduledJob** inte har importer ATS till sessionen.

> [!NOTE]
> Innan du använder en jobb-cmdlet på schemalagda jobb instanser måste du kontrol lera att modulen **PSScheduledJob** ingår i sessionen. Utan modulen **PSScheduledJob** kan inte jobb-cmdlet: ar Hämta schemalagda jobb instanser eller deras resultat.

Så här importerar du **PSScheduledJob** -modulen:

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a>Receive-Job cmdlet kanske redan returnerade resultaten

Om `Receive-Job` resultat för jobb instans inte returneras kan det bero på att ett `Receive-Job` kommando har körts för jobb instansen i den aktuella sessionen utan parametern **Keep** .

Om du använder `Receive-Job` utan parametern **Keep** `Receive-Job` returnerar jobb resultatet och anger **HasMoreData** -egenskapen för jobb instansen till **false**. Värdet **false** innebär att resultatet `Receive-Job` returnerade jobbets resultat och att instansen inte har fler resultat att returnera. Den här inställningen är lämplig för vanliga bakgrunds jobb, men inte för instanser av schemalagda jobb som sparas på disk.

Starta en ny PowerShell-session genom att skriva för att hämta jobb instans resultatet igen `PowerShell` . Importera modulen **PSScheduledJob** och försök att utföra `Receive-Job` kommandot igen.

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a>Använda parametern Keep för att få resultat mer än en gång i en session

Om du vill få resultatet av en jobb instans mer än en gång i en session använder du parametern **Keep** för `Receive-Job` cmdleten.

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a>Det schemalagda jobbet kan vara skadat

Om ett schemalagt jobb skadas tar PowerShell bort det skadade schemalagda jobbet och dess resultat. Det går inte att återställa resultatet av ett skadat schemalagt jobb.

Använd cmdleten för att avgöra om ett schemalagt jobb fortfarande finns `Get-ScheduledJob` .

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a>Antalet resultat kan ha överskridit ExecutionHistoryLength

**ExecutionHistoryLength** -egenskapen för ett schemalagt jobb fastställer hur många jobb instanser och deras resultat som sparas på disk. Standardvärdet är 32.
När antalet instanser av ett schemalagt jobb överstiger detta värde, tar PowerShell bort den äldsta jobb instansen för att göra plats för varje ny jobb instans.

Om du vill hämta värdet för egenskapen **ExecutionHistoryLength** för ett schemalagt jobb använder du följande kommando format:

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

Till exempel hämtar följande kommando värdet för egenskapen **ExecutionHistoryLength** för det schemalagda **ProcessJob** -jobbet.

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

Om du vill ange eller ändra värdet för egenskapen **ExecutionHistoryLength** använder du parametern **MaxResultCount** för `Register-ScheduledJob` `Set-ScheduledJob` cmdletarna och.

Följande kommando ökar värdet för egenskapen **ExecutionHistoryLength** till 50.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a>Resultatet av jobb instansen kan ha tagits bort

Parametern **ClearExecutionHistory** för `Set-ScheduledJob` cmdleten tar bort körnings historiken för ett jobb. Du kan använda den här funktionen för att frigöra disk utrymme eller ta bort resultat som inte behövs, eller som redan används, analyseras eller sparas på en annan plats.

Om du vill ta bort körnings historiken för ett schemalagt jobb använder du parametern **ClearExecutionHistory** för det schemalagda jobbet.

Följande kommando tar bort körnings historiken för det schemalagda **ProcessJob** -jobbet.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

Dessutom `Remove-Job` tar cmdleten bort jobb resultat. När du använder `Remove-Job` för att ta bort ett schemalagt jobb raderas alla instanser av jobbet på disken, inklusive körnings historik och alla jobb resultat.

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a>Jobb som har startats med hjälp av Start-Job cmdlet sparas inte på disken

När du använder `Start-Job` för att starta ett schemalagt jobb `Start-Job` startar ett standard bakgrunds jobb i stället för att använda en jobb utlösare. Bakgrunds jobbet och dess resultat lagras inte i körnings historiken för jobbet på disken.

Du kan använda `Get-Job` cmdleten för att hämta jobbet och `Receive-Job` cmdleten för att hämta jobb resultatet, men resultaten är bara tillgängliga tills du får dem, om du inte använder parametern Keep för `Receive-Job` cmdleten.

Bakgrunds jobb och deras resultat är också sessionsbaserade. de finns bara i den session där de skapas. Om du tar bort jobbet med `Remove-Job` , stänger sessionen eller stänger PowerShell, tas jobb instansen och dess resultat bort.

## <a name="scheduled-job-doesnt-run"></a>Schemalagt jobb körs inte

Schemalagda jobb körs inte automatiskt om jobbet utlöses eller om det schemalagda jobbet är inaktiverat.

Använd `Get-ScheduledJob` cmdleten för att hämta det schemalagda jobbet. Kontrol lera att värdet för egenskapen **Enabled** för det schemalagda jobbet är **Sant**.

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

Använd `Get-JobTrigger` cmdleten för att hämta jobb utlösare för det schemalagda jobbet.
Kontrol lera att värdet för den **aktiverade** egenskapen för jobb utlösaren är **Sant**.

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a>Schemalagda jobb körs inte automatiskt om jobb utlösare är ogiltiga

En jobb utlösare kan till exempel ange ett datum tidigare eller ett datum som inte sker, till exempel den femte måndagen i månaden.

Schemalagda jobb körs inte automatiskt om villkoren för jobb utlösaren eller jobb alternativen inte är uppfyllda.

Till exempel kan ett schemalagt jobb som bara körs när en viss användare loggar in på datorn inte köras om användaren inte loggar in eller endast ansluter via fjärr anslutning.

Granska alternativen för det schemalagda jobbet och se till att de är uppfyllda.
Till exempel ett schemalagt jobb som kräver att datorn är inaktiv eller kräver en nätverks anslutning, eller har en lång **IdleDuration** eller en kort **idleTimeout** kanske aldrig kan köras.

Använd `Get-ScheduledJobOption` cmdleten för att undersöka jobb alternativen och deras värden.

```powershell
Get-ScheduledJob -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Beskrivningar av alternativen för schemalagda jobb finns i [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).

### <a name="the-scheduled-job-instance-might-have-failed"></a>Den schemalagda jobb instansen kan ha misslyckats

Om ett schemalagt jobb-kommando Miss lyckas rapporterar PowerShell direkt genom att generera ett fel meddelande. Men om jobbet Miss lyckas när Schemaläggaren försöker köra det, är felet inte tillgängligt för PowerShell.

Använd följande metoder för att identifiera och korrigera jobb fel:

Kontrol lera om det finns fel i händelse loggen för Schemaläggaren. Om du vill kontrol lera loggen använder Loggboken eller ett PowerShell-kommando, till exempel följande:

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

Kontrol lera jobb posten i Schemaläggaren. Schemalagda PowerShell-jobb lagras i följande schemalagda mapp för aktiviteter:

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a>Det schemalagda jobbet kanske inte kan köras på grund av otillräcklig behörighet

Schemalagda jobb körs med behörigheterna för den användare som skapade jobbet eller behörigheter för den användare som anges av parametern **Credential** i `Register-ScheduledJob` `Set-ScheduledJob` kommandot eller.

Om användaren inte har behörighet att köra kommandona eller skripten Miss lyckas jobbet.

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a>Det går inte att hämta schemalagt jobb eller schemalagt jobb är skadat

I sällsynta fall kan schemalagda jobb skadas eller innehålla interna motstridiga händelser som inte kan lösas. Detta inträffar vanligt vis när XML-filerna för det schemalagda jobbet redige ras manuellt, vilket resulterar i ogiltig XML.

När ett schemalagt jobb skadas försöker PowerShell ta bort det schemalagda jobbet, dess körnings historik och resultatet från disken.

Om det inte går att ta bort det schemalagda jobbet får du ett skadat jobb fel meddelande varje gång du kör `Get-ScheduledJob` cmdleten.

Om du vill ta bort ett skadat schemalagt jobb använder du någon av följande metoder:

Ta bort `<ScheduledJobName>` katalogen för det schemalagda jobbet. Ta inte bort **ScheduledJob** -katalogen.

Katalogens plats:

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

Ett exempel:

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

Använd Schemaläggaren för att ta bort det schemalagda jobbet. Schemalagda aktiviteter för PowerShell visas i följande sökväg för Schemaläggaren:

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a>Jobb-cmdlets kan inte konsekvent hitta schemalagda jobb

När modulen **PSScheduledJob** inte finns i den aktuella sessionen kan inte jobb-cmdlet: ar Hämta schemalagda jobb, starta dem eller få sina resultat.

Importera **PSScheduledJob** -modulen genom att skriva `Import-Module PSScheduledJob` eller köra eller hämta en cmdlet i modulen, till exempel `Get-ScheduledJob` cmdleten.
Från och med PowerShell 3,0 importeras moduler automatiskt när du hämtar eller använder valfri cmdlet i modulen.

När **PSScheduledJob** -modulen inte finns i den aktuella sessionen är följande kommando ordning möjlig.

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

Det här problemet beror på att `Get-ScheduledJob` kommandot automatiskt importerar **PSScheduledJob** -modulen och sedan kör kommandot.

## <a name="see-also"></a>Se även

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul

[Schemaläggaren](/windows/desktop/TaskSchd/task-scheduler-reference)
