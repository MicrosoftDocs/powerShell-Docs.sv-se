---
description: Förklarar hur du skapar och hanterar schemalagda jobb.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270969"
---
# <a name="about-scheduled-jobs-basics"></a>Om grundläggande om schemalagda jobb

## <a name="short-description"></a>Kort beskrivning

Förklarar hur du skapar och hanterar schemalagda jobb.

## <a name="long-description"></a>Lång beskrivning

Det här dokumentet visar hur du utför grundläggande uppgifter för att skapa och hantera schemalagda jobb. Information om mer avancerade uppgifter finns [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).

Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).

## <a name="how-to-create-a-scheduled-job"></a>Så här skapar du ett schemalagt jobb

Använd cmdleten för att skapa ett schemalagt jobb `Register-ScheduledJob` . Cmdleten kräver ett namn och de kommandon eller skript som jobbet kör. Du kan antingen köra jobbet direkt genom att lägga till parametern **RunNow** eller skapa en jobb utlösare och ange jobb alternativ när du skapar jobbet, eller redigera ett befintligt jobb.

Om du vill skapa ett jobb som kör ett skript använder du parametern **sökväg** för att ange sökvägen till skript filen. Om du vill skapa ett jobb som kör kommandon använder du parametern **script block** .

`Register-ScheduledJob`Cmdlet: en skapar **ProcessJob** , som kör ett `Get-Process` kommando. Det här schemalagda jobbet har standard jobb alternativen och ingen jobb utlösare.

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a>Så här skapar du en jobb utlösare

Jobb utlösare startar ett schemalagt jobb automatiskt. En jobb utlösare kan vara ett engångs schema eller ett återkommande schema eller en händelse, till exempel när en användare loggar in eller Windows startas. Varje jobb kan ha noll, ett eller flera jobb utlösare.

Använd cmdleten för att skapa en jobb utlösare `New-JobTrigger` . Följande kommando skapar en jobb utlösare som startar ett jobb varje måndag och torsdag kl. 5:00.
Kommandot sparar jobb utlösaren i `$T` variabeln.

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

Jobb utlösare är valfria. Du kan starta ett schemalagt jobb när som helst genom att lägga till parametern **RunNow** i ditt `Register-ScheduledJob` kommando, eller genom att använda `Start-Job` cmdletarna.

## <a name="how-to-add-a-job-trigger"></a>Så här lägger du till en jobb utlösare

När du lägger till en jobb utlösare i ett schemalagt jobb läggs jobb utlösaren till i det schemalagda jobbets XML-fil för det schemalagda jobbet och blir en del av det schemalagda jobbet.

Du kan lägga till en jobb utlösare i ett schemalagt jobb när du skapar det schemalagda jobbet eller redigera ett befintligt jobb. Du kan när som helst ändra jobb utlösaren för ett schemalagt jobb.

PowerShell använder vissa av de jobb utlösare som Schemaläggaren använder. Detaljerad information om jobb utlösare finns i hjälp avsnittet för cmdleten [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) .

I följande exempel används ihopbuntning för att skapa `$JobParms` som är parameter värden som skickas till `Register-ScheduledJob` cmdleten. Mer information finns i [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).
`Register-ScheduledJob`Använder `@JobParms` för att skapa ett schemalagt jobb. Den använder **Utlösar** -parametern för att ange jobb utlösaren i `$T` variabeln.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

Du kan också lägga till en jobb utlösare till ett befintligt schemalagt jobb när som helst. `Add-JobTrigger`Cmdleten lägger till jobb utlösaren i `$T` variabeln till det schemalagda **ProcessJob** -jobbet.

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

Därför startar jobb utlösaren **ProcessJob** automatiskt varje måndag och torsdag kl. 5:00.

## <a name="how-to-get-a-job-trigger"></a>Så här hämtar du en jobb utlösare

Använd cmdleten för att hämta jobb utlösaren för ett schemalagt jobb `Get-JobTrigger` . Använd parametrarna **Name** , **ID** och **InputObject** för att ange det schemalagda jobbet, inte jobb utlösaren.

`Get-JobTrigger` hämtar jobb utlösaren för **ProcessJob**.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a>Så här skapar du jobb alternativ

Jobb alternativ fastställer villkor för att starta och köra jobbet. Varje jobb har standard jobb alternativ om du inte ändrar dem. Eftersom jobb alternativ kan förhindra att ett jobb körs vid den schemalagda tiden är det viktigt att förstå jobb alternativen och använda dem noggrant.

PowerShell använder samma jobb alternativ som Schemaläggaren använder. Detaljerad information om jobb alternativen finns i hjälp avsnittet för [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).

Jobb alternativen lagras i XML-filen med schemalagt jobb. Du kan ange jobb alternativ när du skapar ett schemalagt jobb eller ändrar dem när som helst.

`New-ScheduledJobOption`Cmdleten skapar ett schemalagt jobb-alternativ där alternativet **WakeToRun** schemalagt jobb är inställt på True. Alternativet **WakeToRun** kör det schemalagda jobbet även om datorn är i vilo läge eller vilo läge vid den schemalagda start tiden. Kommandot sparar jobb alternativen i `$O` variabeln.

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a>Så här hämtar du jobb alternativ

Använd cmdleten för att hämta jobb alternativen för ett schemalagt jobb `Get-ScheduledJobOption` . Använd parametrarna **Name** , **ID** och **InputObject** för att ange det schemalagda jobbet, inte jobb alternativen.

`Get-ScheduledJobOption` hämtar jobb alternativen för **ProcessJob**.

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
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

## <a name="how-to-change-job-options"></a>Ändra jobb alternativ

Du kan ändra jobb alternativen för ett schemalagt jobb när du skapar ett schemalagt jobb eller redigera ett befintligt jobb.

Splatted `$JobParms` skickas till `Add-JobTrigger` cmdlet: en för att skapa process jobbet. Parametern **ScheduledJobOption** används för att ange jobb alternativen i `$O` variabeln.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

Du kan också ändra jobb alternativen till ett befintligt schemalagt jobb när som helst.
Följande kommando använder `Set-ScheduledJobOption` cmdleten för att ändra värdet för alternativet **WakeToRun** för **ProcessJob** scheduledJob till **True**.

`Set`Cmdletarna i **PSScheduledJob** -modulen, t. ex. `Set-ScheduledJobOption` cmdlet, har inte **namn** **-eller ID-** parametrar. Du kan använda parametern **InputObject** för att ange de schemalagda jobb alternativen eller skicka ett schemalagt jobb från `Get-ScheduledJobOption` cmdlet till `Set-ScheduledJobOption` .

I det här exemplet används `Get-ScheduledJob` cmdlet: en för att hämta ProcessJob. Den använder `Get-ScheduledJobOption` cmdleten för att hämta jobb alternativen i **ProcessJob** och `Set-ScheduledJobOption` cmdleten för att ändra **WakeToRun** -jobbets alternativ i ProcessJob till true.

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a>Så här hämtar du schemalagda jobb instanser

När ett schemalagt jobb startas skapar PowerShell en jobb instans som liknar ett standard bakgrunds jobb i PowerShell. Du kan använda jobb-cmdletar, till exempel `Get-Job` `Stop-Job` och `Receive-Job` för att hantera jobb instanser.

> [!NOTE]
> Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen. Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .

Om du vill hämta alla instanser av schemalagda PowerShell-jobb och alla aktiva standard jobb använder du `Get-Job` cmdleten. `Import-Module`Cmdleten importerar modulen **PSScheduledJob** och `Get-Job` hämtar jobben på den lokala datorn.

```powershell
Import-Module PSScheduledJob
Get-Job
```

`Get-Job` hämtar instanser av **ProcessJob** på den lokala datorn.

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

Standard visningen visar inte start tiden, vilket normalt särskiljer instanser av samma schemalagda jobb.

`Get-Job`Cmdleten skickar objekt nedåt i pipelinen. `Format-Table`Cmdleten visar egenskaperna **namn** , **ID** och **BeginTime** för det schemalagda jobbet.

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
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

## <a name="get-scheduled-job-results"></a>Hämta schemalagt jobb resultat

Använd cmdleten för att hämta resultatet av en instans av ett schemalagt jobb `Receive-Job` .

> [!NOTE]
> Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen. Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .

I det här exemplet får du resultatet från den senaste instansen av det schemalagda **ProcessJob** -jobbet (ID = 51).

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

Resultatet av schemalagda jobb sparas på disk, så parametern **Keep** of `Receive-Job` är inte obligatorisk. Men utan parametern **Keep** kan du bara hämta resultatet av ett schemalagt jobb en gång i varje PowerShell-session. Starta en ny PowerShell-session genom att skriva `PowerShell` eller öppna ett nytt PowerShell-fönster.

## <a name="see-also"></a>Se även

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul

[Schemaläggaren](/windows/desktop/TaskSchd/task-scheduler-reference)
