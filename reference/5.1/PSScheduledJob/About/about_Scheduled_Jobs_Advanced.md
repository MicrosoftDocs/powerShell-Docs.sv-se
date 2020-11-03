---
description: Beskriver de avancerade ämnena för schemalagda jobb, inklusive fil strukturen som är beroende av de schemalagda jobben.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270975"
---
# <a name="about-scheduled-jobs-advanced"></a>Om schemalagda uppgifter avancerade

## <a name="short-description"></a>Kort beskrivning

Beskriver de avancerade ämnena för schemalagda jobb, inklusive fil strukturen som är beroende av de schemalagda jobben.

## <a name="long-description"></a>Lång beskrivning

Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).

## <a name="scheduled-job-directories-and-files"></a>Schemalagda jobb kataloger och filer

Schemalagda PowerShell-jobb är både PowerShell-jobb och Task Scheduler-aktiviteter.
Varje schemalagt jobb registreras i Schemaläggaren och sparas på disken i Microsoft .NET Framework serialisera XML-format.

När du skapar ett schemalagt jobb skapar PowerShell en katalog för det schemalagda jobbet i `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` katalogen på den lokala datorn. Katalog namnet är detsamma som jobb namnet.

Följande är ett exempel på en **ScheduledJobs** -katalog.

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

Varje schemalagt jobb har sin egen katalog. Katalogen innehåller den schemalagda XML-filen och en under katalog för **utdata** .

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

Den **resulterande** katalogen för ett schemalagt jobb innehåller dess körnings historik.
Varje gång en jobb utlöses startar ett schemalagt jobb skapar PowerShell en tidsstämpel-namngiven katalog i utdatakatalogen. Katalogen timestamp innehåller resultatet av jobbet i en **Results.xml** -fil och jobb status i en **Status.xml** -fil.

Följande kommando visar katalogerna för körnings historik för det schemalagda **ProcessJob** -jobbet.

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

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

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

Du kan öppna och granska **ScheduledJobDefinition.xml** , **Results.xml** och **Status.xml** filer eller använda `Select-XML` cmdleten för att parsa filerna.

> [!WARNING]
> Redigera inte XML-filerna. Om en XML-fil innehåller ogiltig XML, tar PowerShell bort det schemalagda jobbet och dess körnings historik, inklusive jobb resultat.

## <a name="start-a-scheduled-job-immediately"></a>Starta ett schemalagt jobb omedelbart

Du kan starta ett schemalagt jobb direkt på något av två sätt:

- Kör `Start-Job` cmdleten för att starta ett schemalagt jobb.
- Lägg till parametern **RunNow** i `Register-ScheduledJob` kommandot för att starta jobbet så snart kommandot körs.

Jobb som har startats med hjälp av `Start-Job` cmdleten är vanliga PowerShell-bakgrunds jobb, inte instanser av det schemalagda jobbet. Precis som alla bakgrunds jobb startar de här jobben omedelbart, de omfattas inte av jobb alternativ eller påverkas av jobb utlösare. Jobbets utdata sparas inte i katalogen **utdata** i katalogen för schemalagda jobb.

Följande kommando använder **DefinitionName** -parametern för `Start-Job` cmdleten för att starta det schemalagda ProcessJob-jobbet.

```powershell
Start-Job -DefinitionName ProcessJob
```

Använd jobb-cmdletar för att hantera jobbet och hämta jobb resultatet. Mer information om jobb-cmdlets finns i [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).

> [!NOTE]
> Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen. Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .

## <a name="rename-a-scheduled-job"></a>Byta namn på ett schemalagt jobb

Om du vill byta namn på ett schemalagt jobb använder du parametern name i `Set-ScheduledJob` cmdleten. När du byter namn på ett schemalagt jobb ändrar PowerShell namnet på det schemalagda jobbet och den schemalagda jobb katalogen. Den ändrar dock inte namnen på instanser av det schemalagda jobbet som redan har körts.

## <a name="get-start-and-end-times"></a>Hämta start-och slut tider

Använd egenskaperna **PSBeginTime** och **PSEndTime** för ScheduledJob-objektet som returnerar schemalagda jobb för att hämta datum och tider då jobb instanser startade och slutar `Get-Job` .

I följande exempel används **egenskaps** parametern för `Format-Table` cmdleten för att visa egenskaperna **PSBeginTime** och **PSEndTime** för varje jobb instans i en tabell. En beräknad egenskap med namnet **etikett** visar den förflutna tiden för varje jobb instans.

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a>Hantera körnings historik

Du kan bestämma antalet jobb instans resultat som sparas för varje schemalagt jobb och ta bort körnings historiken och de sparade jobb resultaten för schemalagda jobb.

**ExecutionHistoryLength** -egenskapen för ett schemalagt jobb fastställer hur många jobb instans resultat som sparas för det schemalagda jobbet. När antalet sparade resultat överskrider värdet för egenskapen **ExecutionHistoryLength** , tar PowerShell bort resultatet från den äldsta instansen för att göra plats för resultatet av den senaste instansen.

Som standard sparar PowerShell körnings historiken och resultaten av 32 instanser av varje schemalagt jobb. Om du vill ändra värdet använder du **MaxResultCount** -parametrarna för `Register-ScheduledJob` `Set-ScheduledJob` cmdletarna eller.

Om du vill ta bort körnings historiken och alla resultat för ett schemalagt jobb använder du parametern **ClearExecutionHistory** för `Set-ScheduledJob` cmdleten. Om du tar bort den här körnings historiken hindras inte PowerShell från att spara resultaten av nya instanser av det schemalagda jobbet.

I följande exempel används ihopbuntning för att skapa `$JobParms` som är parameter värden som skickas till `Register-ScheduledJob` cmdleten. Mer information finns i [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).
`Register-ScheduledJob`Använder `@JobParms` för att skapa ett schemalagt jobb. Kommandot använder parametern **MaxResultCount** med värdet 12 för att endast spara de 12 nyaste jobb instans resultaten för det schemalagda jobbet.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

Följande kommando använder **MaxResultCount** -parametern för `Set-ScheduledJob` cmdleten för att öka antalet sparade instans resultat till
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

Följande kommando tar bort körnings historiken och de aktuella sparade resultaten för det schemalagda **ProcessJob** -jobbet.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

Följande kommando hämtar värdena för namn-och **ExecutionHistoryLength** -egenskaperna för alla schemalagda jobb på datorn och visar dem i en tabell.

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a>Se även

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul

[Schemaläggaren](/windows/desktop/TaskSchd/task-scheduler-reference)
