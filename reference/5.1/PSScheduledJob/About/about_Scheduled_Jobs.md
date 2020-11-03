---
description: Beskriver schemalagda jobb och förklarar hur du använder och hanterar schemalagda jobb i PowerShell och i Schemaläggaren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270980"
---
# <a name="about-scheduled-jobs"></a>Om schemalagda jobb

## <a name="short-description"></a>Kort beskrivning

Beskriver schemalagda jobb och förklarar hur du använder och hanterar schemalagda jobb i PowerShell och i Schemaläggaren.

## <a name="long-description"></a>Lång beskrivning

Schemalagda PowerShell-jobb är en användbar hybrid av PowerShell-arbetsjobb och Schemaläggaren-aktiviteter.

Som till exempel PowerShell-bakgrunds jobb körs schemalagda jobb asynkront i bakgrunden. Instanser av schemalagda jobb som har körningar kan hanteras med hjälp av jobb-cmdletarna, till exempel,, `Start-Job` `Get-Job` `Stop-Job` och `Receive-Job` .

Som aktiviteter i Schemaläggaren sparas schemalagda jobb till disk. Du kan visa och hantera jobben i Schemaläggaren, aktivera och inaktivera dem efter behov, köra dem eller använda dem som mallar, upprätta ett engångs-eller återkommande schema för att starta jobben eller ange under vilka omständigheter jobben ska starta.

Dessutom sparas resultatet av schemalagda jobb instanser till disk i ett enkelt och lättillgängligt format, vilket ger en pågående logg över jobbets utdata. Schemalagda jobb levereras med en anpassad uppsättning cmdlets för att hantera dem. Med cmdletarna kan du skapa, redigera, hantera, inaktivera och återaktivera schemalagda jobb, jobb utlösare och jobb alternativ.

Den här omfattande och flexibla uppsättningen verktyg gör schemalagda jobb till en viktig komponent i många IT-lösningar för Professional PowerShell.

De schemalagda jobb-cmdletarna ingår i **PSScheduledJob** -modulen som installeras med PowerShell. Den här modulen introducerades i PowerShell 3,0 och fungerar i PowerShell 3,0 och senare versioner av PowerShell. Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).

Mer information om PowerShell-bakgrunds jobb finns [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).

Mer information [om Schemaläggaren finns i](/windows/desktop/TaskSchd/task-scheduler-reference)Schemaläggaren.

> [!NOTE]
> Du kan visa och hantera schemalagda PowerShell-jobb i Schemaläggaren. PowerShell-jobben och de schemalagda jobb-cmdletarna fungerar bara för schemalagda jobb som skapas i PowerShell.

## <a name="quick-start"></a>Snabbstart

I det här exemplet skapas ett schemalagt jobb som börjar varje dag kl. 3:00 och kör `Get-Process` cmdleten. Jobbet startar även om datorn körs på batterier.

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

`Get-ScheduledJob`Cmdlet: en hämtar de schemalagda jobben på den lokala datorn.

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

`Get-JobTrigger` hämtar jobb utlösare för **ProcessJob**. Indataparametrarna anger det schemalagda jobbet, inte utlösaren, eftersom utlösare sparas i ett schemalagt jobb.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

I det här exemplet används parametern **ContinueIfGoingOnBattery** för `Set-ScheduledJob` cmdleten för att ändra egenskapen **StopIfGoingOnBatteries** för **ProcessJob** till **false**.

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
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

`Get-ScheduledJob`Cmdlet: en hämtar det schemalagda **ProcessJob** -jobbet.

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

`Get-Job`Cmdleten hämtar alla instanser av det schemalagda **ProcessJob** -jobbet som har körts hittills. `Get-Job`Cmdlet: en hämtar endast schemalagda jobb när **PSScheduledJob** -modulen importeras till den aktuella sessionen.

> [!TIP]
> Observera att du använder de schemalagda jobb-cmdletarna för att hantera schemalagda jobb, men du använder jobb-cmdletar för att hantera instanser av schemalagda jobb.

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

`Receive-Job`Cmdlet: en hämtar resultatet från den senaste instansen av det schemalagda **ProcessJob** -jobbet (ID = 51).

```powershell
Receive-Job -ID 51
```

Även om `Receive-Job` kommandot inte inkluderade parametern **Behåll** , sparas resultatet av jobbet på disken tills du tar bort dem eller så har det maximala antalet resultat överskridits.

Jobb resultatet är inte längre tillgängligt i den här sessionen, men om du startar en ny session eller öppnar ett nytt PowerShell-fönster är resultatet av jobbet tillgängligt igen.

Följande kommando använder **DefinitionName** -parametern för `Start-Job` cmdleten för att starta det schemalagda **ProcessJob** -jobbet.

Jobb som har startats med hjälp av `Start-Job` cmdleten är vanliga PowerShell-bakgrunds jobb, inte instanser av det schemalagda jobbet. Precis som alla bakgrunds jobb startar de här jobben omedelbart, de omfattas inte av jobb alternativ eller påverkas av jobb utlösare och deras utdata sparas inte i katalogen utdata i den schemalagda jobb katalogen.

```powershell
Start-Job -DefinitionName ProcessJob
```

`Unregister-ScheduledJob`Cmdleten tar bort det schemalagda **ProcessJob** -jobbet och alla sparade resultat från jobb instanserna.

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a>Metoder för schemalagda jobb

Ett schemalagt jobb kör kommandon eller ett skript. Ett schemalagt jobb kan innehålla jobb utlösare som startar jobb-och jobb alternativen som anger villkor för körning av jobbet.

En jobb utlösare startar ett schemalagt jobb automatiskt. En jobb utlösare kan inkludera ett engångs schema eller ett återkommande schema eller ange en händelse, till exempel när en användare loggar in eller Windows startas. Ett schemalagt jobb kan ha en eller flera jobb utlösare, och du kan skapa, lägga till, aktivera, inaktivera och hämta jobb utlösare.

Jobb utlösare är valfria. Du kan starta schemalagda jobb direkt med hjälp av `Start-Job cmdlet` , eller genom att lägga till **RunNow** -parametern i `Register-ScheduledJob` kommandot.

Jobb alternativ anger villkoren för att köra ett schemalagt jobb. Varje schemalagt jobb har ett objekt för jobb alternativ. Du kan skapa och redigera jobb alternativ objekt och lägga till dem i en eller flera schemalagda jobb.

Varje gång ett schemalagt jobb startas skapas en jobb instans. Använd cmdletar för PowerShell-jobb för att visa och hantera jobb instansen.

Schemalagda jobb sparas till disk och använder cmdlet-verbet, `Register` i stället för `New` . XML-filerna finns på den lokala datorn i katalogen `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .

PowerShell skapar en katalog för varje schemalagt jobb och sparar jobb kommandona, jobb utlösare, jobb alternativ och jobb resultat i den schemalagda jobb katalogen. Jobb utlösare och jobb alternativ sparas inte på disken oberoende av varandra.
De sparas i XML-koden för schemalagda jobb för varje schemalagt jobb som de är associerade med.

Schemalagda jobb, jobb utlösare och jobb alternativ visas i PowerShell som objekt.
Objekten är sammanlänkade, vilket gör det enkelt att identifiera och använda i kommandon och skript.

Schemalagda uppgifter visas som **ScheduledJobDefinition** -objekt. **ScheduledJobDefinition** -objektet har en **JobTriggers** -egenskap som innehåller jobb utlösare för det schemalagda jobbet och en **alternativ** egenskap som innehåller jobb alternativen. **ScheduledJobTriggers** -och **ScheduledJobOptions** -objekten som representerar jobb utlösare och jobb alternativ, var och en har en **jobb definitionen** -egenskap som innehåller det schemalagda jobb som de är associerade med. Den här rekursiva sammanlänkningen gör det enkelt att hitta utlösare och alternativ för ett schemalagt jobb och att söka efter, skripta och visa det schemalagda jobbet som en jobb utlösare eller ett jobb alternativ är associerat med.

## <a name="see-also"></a>Se även

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul

[Schemaläggaren](/windows/desktop/TaskSchd/task-scheduler-reference)
