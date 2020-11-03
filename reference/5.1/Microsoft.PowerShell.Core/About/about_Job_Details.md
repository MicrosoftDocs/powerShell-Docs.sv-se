---
description: Innehåller information om bakgrunds jobb på lokala datorer och fjärrdatorer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: cd6c633e9f409054b0ee89021de961c36d84ac3b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2020
ms.locfileid: "93272955"
---
# <a name="about-job-details"></a>Om jobb information

## <a name="short-description"></a>Kort beskrivning
Innehåller information om bakgrunds jobb på lokala datorer och fjärrdatorer.

## <a name="detailed-description"></a>Detaljerad beskrivning

Det här avsnittet beskriver konceptet med ett bakgrunds jobb och ger teknisk information om hur bakgrunds jobb fungerar i PowerShell.

Det här avsnittet är ett tillägg till avsnitten [about_Jobs](about_Jobs.md), [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)och [about_Remote_Jobs](about_Remote_Jobs.md) .

### <a name="about-background-jobs"></a>Om bakgrunds jobb

Ett bakgrunds jobb kör ett kommando eller uttryck asynkront. Det kan köra en cmdlet, en funktion, ett skript eller någon annan kommando-baserad uppgift. Den är utformad för att köra kommandon som tar en längre tid, men du kan använda det för att köra alla kommandon i bakgrunden.

När ett synkront kommando körs, ignoreras PowerShell-Kommandotolken tills kommandot har slutförts. Men ett bakgrunds jobb förhindrar inte PowerShell-prompten. Ett kommando för att starta ett bakgrunds jobb returnerar ett jobb objekt.
Prompten återgår direkt så att du kan arbeta med andra uppgifter medan bakgrunds jobbet körs.

När du startar ett bakgrunds jobb får du dock inte resultaten direkt även om jobbet körs mycket snabbt. Jobbobjektet som returneras innehåller användbar information om jobbet, men det innehåller inte jobb resultatet. Du måste köra ett separat kommando för att hämta jobb resultatet. Du kan också köra kommandon för att stoppa jobbet, vänta tills jobbet har slutförts och ta bort jobbet.

För att göra tids inställningen för ett bakgrunds jobb oberoende av andra kommandon körs varje bakgrunds jobb i en egen PowerShell-session. Det kan dock vara en tillfällig anslutning som bara skapas för att köra jobbet och sedan destrueras, eller så kan det vara en permanent **PSSession** som du kan använda för att köra flera relaterade jobb eller kommandon.

### <a name="using-the-job-cmdlets"></a>Använda jobb-cmdletar

Använd ett `Start-Job` kommando för att starta ett bakgrunds jobb på en lokal dator.
`Start-Job` Returnerar ett jobb objekt. Du kan också hämta objekt som representerar de jobb som startades på den lokala datorn med hjälp av `Get-Job` cmdleten.

Hämta jobb resultaten med hjälp av ett `Receive-Job` kommando. Om jobbet inte är klart `Receive-Job` returneras delvis resultat. Du kan också använda `Wait-Job` cmdleten för att ignorera kommando tolken tills ett eller flera av jobben som startades i sessionen har slutförts.

Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten. Använd cmdleten om du vill ta bort ett jobb `Remove-Job` .

Mer information om hur cmdletarna fungerar finns i hjälp avsnittet för varje cmdlet och se [about_Jobs](about_Jobs.md).

### <a name="starting-background-jobs-on-remote-computers"></a>Starta bakgrunds jobb på fjärrdatorer

Du kan skapa och hantera bakgrunds jobb på en lokal dator eller fjärrdator. Om du vill köra ett bakgrunds jobb via en fjärr anslutning använder du parametern **AsJob** för en cmdlet, till exempel `Invoke-Command` eller använder `Invoke-Command` cmdleten för att fjärrköra ett `Start-Job` kommando. Du kan också starta ett bakgrunds jobb i en interaktiv session.

Mer information om fjärran sluten bakgrunds jobb finns [about_Remote_Jobs](about_Remote_Jobs.md).

### <a name="child-jobs"></a>Underordnade jobb

Varje bakgrunds jobb består av ett överordnat jobb och ett eller flera underordnade jobb. I jobb som har startats med `Start-Job` eller **AsJob** -parametern för `Invoke-Command` är det överordnade jobbet en chef. Inga kommandon körs eller inga resultat returneras. Kommandona körs faktiskt av de underordnade jobben. Jobb som startas med andra cmdlets kan fungera annorlunda.

De underordnade jobben lagras i egenskapen **ChildJobs** för objektet överordnat jobb. Egenskapen **ChildJobs** kan innehålla ett eller flera underordnade jobb objekt.
De underordnade jobb objekten har ett **namn** , **ID** och **InstanceID** som skiljer sig från det överordnade jobbet så att du kan hantera de överordnade och underordnade jobben individuellt eller som en enhet.

Om du vill hämta de överordnade och underordnade jobben för ett jobb använder du parametern **IncludeChildJobs** för `Get-Job` cmdleten. **IncludeChildJob** -parametern introducerades i Windows PowerShell 3,0.

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Använd parametern **ChildJobState** för cmdleten om du vill hämta det överordnade jobbet och bara de underordnade jobben med ett visst **tillstånds** värde `Get-Job` . **ChildJobState** -parametern introducerades i Windows PowerShell 3,0.

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Använd egenskapen **ChildJob** för det överordnade jobbet för att hämta de underordnade jobben för ett jobb i alla versioner av PowerShell.

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Du kan också använda ett `Get-Job` kommando på det underordnade jobbet, som du ser i följande kommando:

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

Konfigurationen av det underordnade jobbet beror på vilket kommando du använder för att starta jobbet.

- När du använder `Start-Job` för att starta ett jobb på en lokal dator består jobbet av ett överordnat överordnat jobb och ett underordnat jobb som kör kommandot.

- När du använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb på en eller flera datorer består jobbet av ett överordnat överordnat jobb och ett underordnat jobb för varje jobb körning på varje dator.

- När du använder `Invoke-Command` för att köra ett `Start-Job` kommando på en eller flera fjärrdatorer är resultatet detsamma som en lokal kommando körning på varje fjärrdator. Kommandot returnerar ett jobb objekt för varje dator. Jobbobjektet består av ett överordnat överordnat jobb och ett underordnat jobb som kör kommandot.

Det överordnade jobbet representerar alla underordnade jobb. När du hanterar ett överordnat jobb hanterar du även de associerade underordnade jobben. Om du till exempel stoppar ett överordnat jobb stoppas alla underordnade jobb. Om du får resultatet av ett överordnat jobb får du resultatet av alla underordnade jobb.

Du kan dock även hantera underordnade jobb individuellt. Detta är mest användbart när du vill undersöka ett problem med ett jobb eller hämta resultatet av ett antal underordnade jobb som har startats med hjälp av parametern **AsJob** i `Invoke-Command` .

Följande kommando använder **AsJob** -parametern för `Invoke-Command` för att starta bakgrunds jobb på den lokala datorn och två fjärrdatorer. Kommandot sparar jobbet i `$j` variabeln.

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

När du visar egenskaperna för namn och **ChildJob** för jobbet i `$j` , visar det att kommandot returnerade ett jobb objekt med tre underordnade jobb, ett för varje dator.

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

När du visar det överordnade jobbet visar det att jobbet misslyckades.

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

Men när du kör ett `Get-Job` kommando som hämtar underordnade jobb, visar utdata att det bara finns ett underordnat jobb.

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

Om du vill hämta resultatet av alla underordnade jobb använder du `Receive-Job` cmdleten för att hämta resultatet från det överordnade jobbet. Men du kan också hämta resultatet av ett visst underordnat jobb, som du ser i följande kommando.

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

Med de underordnade jobben i PowerShell bakgrunds jobb får du mer kontroll över de jobb som du kör.

### <a name="job-types"></a>Jobbtyper

PowerShell stöder olika typer av jobb för olika aktiviteter. Från och med Windows PowerShell 3,0 kan utvecklare skriva "jobb käll kort" som lägger till nya jobb typer till PowerShell och inkluderar jobb käll korten i moduler.
När du importerar modulen kan du använda den nya jobb typen i sessionen.

PSScheduledJob-modulen lägger till exempel till schemalagda jobb och modulen PSWorkflow lägger till arbets flödes jobb.

Anpassade jobb typer kan variera avsevärt från vanliga PowerShell-standardjobb. Schemalagda jobb sparas till exempel på disk. de finns inte bara i en viss session. Arbets flödes jobb kan pausas och återupptas.

De cmdletar som du använder för att hantera anpassade jobb beror på jobb typen. För vissa, använder du standard jobb-cmdlet: ar, till exempel `Get-Job` och `Start-Job` . Andra har särskilda cmdletar som endast hanterar en viss typ av jobb. Detaljerad information om anpassade jobb typer finns i hjälp avsnitten om jobb typen.

Använd cmdleten för att hitta jobb typen för ett jobb `Get-Job` . `Get-Job` returnerar olika jobb objekt för olika typer av jobb. Värdet för egenskapen **PSJobTypeName** för de jobb objekt som `Get-Job` returnerar anger jobb typen.

I följande tabell visas de jobb typer som ingår i PowerShell.

|    Jobbtyp    |                       Beskrivning                        |
| -------------- | -------------------------------------------------------- |
| BackgroundJob  | Startade med `Start-Job` cmdleten.                    |
| RemoteJob      | Startade med **AsJob** -parametern för             |
|                | `Invoke-Command` kommandon.                                 |
| PSWorkflowJob  | Startade med **AsJob** -parametern för ett arbets flöde.     |
| PSScheduledJob | En instans av ett schemalagt jobb startades av en jobb utlösare. |
| CIMJob         | Startade med **AsJob** -parametern för en cmdlet från en |
|                | CDXLM-modul.                                            |
| WMIJob         | Startade med **AsJob** -parametern för en cmdlet från en |
|                | WMI-modul.                                              |
| PSEventJob     | Skapad med `Register-ObjectEvent` och ange en    |
|                | åtgärd med **Åtgärds** parametern.                    |

Obs: innan du använder `Get-Job` cmdleten för att hämta jobb av en viss typ, kontrollerar du att modulen som lägger till jobb typen importeras till den aktuella sessionen.
Annars `Get-Job` kommer inte jobb av den typen.

## <a name="examples"></a>Exempel

Följande kommandon skapar ett lokalt bakgrunds jobb, ett fjärran slutet bakgrunds jobb, ett arbets flödes jobb och ett schemalagt jobb. Sedan använder den `Get-Job` cmdleten för att hämta jobben. `Get-Job` får inte det schemalagda jobbet, men alla startade instanser av det schemalagda jobbet hämtas.

Starta ett bakgrunds jobb på den lokala datorn.

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

Starta ett bakgrunds jobb som körs på en fjärrdator.

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

Skapa ett schemalagt jobb

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

Skapa ett arbets flöde.

```powershell
PS> workflow Test-Workflow {Get-Process}
```

Kör arbets flödet som ett jobb.

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

Hämta jobben. `Get-Job`Kommandot kan inte utföra schemalagda jobb, men det hämtar instanser av det schemalagda jobbet som har startats.

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

Använd cmdleten för att hämta schemalagda jobb `Get-ScheduledJob` .

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a>Se även

- [about_Jobs](about_Jobs.md)
- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](/powershell/module/microsoft.powershell.core/about/about_Thread_Jobs)
- [about_Remote](about_Remote.md)
- [Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start – jobb](xref:Microsoft.PowerShell.Core.Start-Job)
- [Hämta jobb](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stoppa – jobb](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Ta bort – jobb](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Avsluta-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
