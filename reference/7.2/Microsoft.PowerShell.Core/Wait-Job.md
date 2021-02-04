---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: ffcd0fba9fae9ed49e7f20fa5a971e6e50fc445f
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098636"
---
# Wait-Job

## SAMMANFATTNING
Väntar tills ett eller flera av de PowerShell-jobb som körs i sessionen är i ett avslutande tillstånd.

## SYNTAX

### SessionIdParameterSet (standard)

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### JobParameterSet

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### NameParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### StateParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## BESKRIVNING

`Wait-Job`Cmdleten väntar på att ett jobb ska vara i ett avslutande tillstånd innan körningen fortsätter.
De avslutande tillstånden är:

- Slutförd
- Misslyckad
- Stoppad
- Inaktiverad
- Frånkopplad

Du kan vänta tills ett visst jobb eller att alla jobb är i ett avslutande tillstånd. Du kan också ange en maximal vänte tid för jobbet med hjälp av parametern **timeout** , eller använda **Force** -parametern för att vänta på ett jobb i `Suspended` eller- `Disconnected` tillstånd.

När kommandona i jobbet har slutförts, `Wait-Job` returnerar ett jobb objekt och fortsätter körningen.

Du kan använda `Wait-Job` cmdleten för att vänta tills jobben har startats med hjälp av `Start-Job` cmdleten eller **AsJob** -parametern för `Invoke-Command` cmdleten. Mer information om jobb finns i [about_Jobs](./about/about_Jobs.md).

Från och med Windows PowerShell 3,0 `Wait-Job` väntar cmdleten även på anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb. Om du vill kunna `Wait-Job` vänta på jobb av en viss typ importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör `Get-Job` cmdleten, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen. Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.

## EXEMPEL

### Exempel 1: vänta på alla jobb

```powershell
Get-Job | Wait-Job
```

Det här kommandot väntar på att alla jobb som körs i sessionen ska slutföras.

### Exempel 2: vänta tills jobben har startats på fjärrdatorer med hjälp av Start-Job

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på fjärrdatorer med hjälp av `Start-Job` cmdleten. Både- `Start-Job` och- `Wait-Job` kommandon skickas till fjärrdatorn med hjälp av `Invoke-Command` cmdleten.

I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Date` kommando som körs som ett jobb på tre olika datorer är klart.

Det första kommandot skapar en Windows PowerShell-session (**PSSession**) på var och en av de tre fjärrdatorerna och lagrar dem i `$s` variabeln.

Det andra kommandot använder `Invoke-Command` för att köra `Start-Job` i var och en av de tre sessionerna i `$s` .
Alla jobb har namnet datum1.

Det tredje kommandot använder `Invoke-Command` för att köra `Wait-Job` . Det här kommandot väntar på `Date1` att jobben på varje dator ska slutföras. Den innehåller den resulterande samlingen (**matris**) för **jobb** objekt i `$done` variabeln.

Det fjärde kommandot använder egenskapen **Count** i matrisen med jobb objekt i `$done` variabeln för att fastställa hur många av jobben som är klara.

### Exempel 3: Bestäm när det första jobbet slutförs

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

I det här exemplet används **valfri** parameter för `Wait-Job` för att fastställa när den första av många jobb som körs i den aktuella sessionen är i ett tillstånd där det avslutas. Det visar också hur du använder `Wait-Job` cmdleten för att vänta på att fjärrjobben ska slutföras.

Det första kommandot skapar en **PSSession** på varje dator som anges i Machines.txt-filen och lagrar **PSSession** -objekt i `$s` variabeln. Kommandot använder `Get-Content` cmdleten för att hämta innehållet i filen. `Get-Content`Kommandot omges av parenteser för att kontrol lera att det körs före `New-PSSession` kommandot.

Det andra kommandot lagrar en `Get-EventLog` kommando sträng, inom citat tecken, i `$c` variabeln.

Det tredje kommandot använder `Invoke-Command` cmdlet för att köras `Start-Job` i varje session i `$s` .
`Start-Job`Kommandot startar ett jobb som kör `Get-EventLog` kommandot i `$c` variabeln.

Kommandot **använder omfångs** modifieraren för att indikera att `$c` variabeln har definierats på den lokala datorn. Omfångs modifieraren **använder** introduceras i Windows PowerShell 3,0. Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./about/about_Remote_Variables.md).

Det fjärde kommandot använder `Invoke-Command` för att köra ett `Wait-Job` kommando i sessionerna. Den använder **valfri** parameter för att vänta tills det första jobbet på fjärrdatorerna avslutas.

### Exempel 4: Ange en vänte tid för jobb på fjärrdatorer

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

Det här exemplet visar hur du använder **timeout** -parametern för `Wait-Job` för att ange en maximal vänte tid för de jobb som körs på fjärrdatorer.

Det första kommandot skapar en **PSSession** på var och en av de tre fjärrdatorerna (Server01, Server02 och Server03) och lagrar sedan **PSSession** -objekten i `$s` variabeln.

Det andra kommandot använder `Invoke-Command` för att köras `Start-Job` i varje **PSSession** -objekt i `$s` . Den lagrar de resulterande jobb objekten i `$jobs` variabeln.

Det tredje kommandot använder `Invoke-Command` för att köras `Wait-Job` i varje session i `$s` . `Wait-Job`Kommandot avgör om alla kommandon har slutförts inom 30 sekunder. Parametern **timeout** används med ett värde på 30 för att fastställa den maximala vänte tiden och lagrar sedan resultatet av kommandot i `$done` variabeln.

I det här fallet är det bara kommandot på Server02-datorn som har slutförts efter 30 sekunder. `Wait-Job` avslutar väntan, returnerar objektet som representerar jobbet som slutförts och visar kommando tolken.

`$done`Variabeln innehåller ett jobb objekt som representerar jobbet som kördes på Server02.

### Exempel 5: vänta tills ett av flera jobb har slutförts

```powershell
Wait-Job -id 1,2,5 -Any
```

Det här kommandot identifierar tre jobb efter deras ID och väntar tills någon av dem är i ett avslutande tillstånd. Körningen fortsätter när det första jobbet är klart.

### Exempel 6: vänta i en period och Tillåt sedan att jobbet fortsätter i bakgrunden

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

Det här kommandot väntar 120 sekunder (två minuter) för att DailyLog-jobbet ska slutföras. Om jobbet inte slutförs under de kommande två minuterna fortsätter körningen och jobbet fortsätter att köras i bakgrunden.

### Exempel 7: vänta på ett jobb efter namn

```powershell
Wait-Job -Name "Job3"
```

Det här kommandot använder jobb namnet för att identifiera det jobb som ska vänta.

### Exempel 8: vänta tills jobb på den lokala datorn har startats med Start-Job

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på den lokala datorn med hjälp av `Start-Job` .

Kommandona startar ett jobb som hämtar Windows PowerShell-skriptfilerna som har lagts till eller uppdaterats under den senaste veckan.

Det första kommandot använder `Start-Job` för att starta ett jobb på den lokala datorn. Jobbet kör ett `Get-ChildItem` kommando som hämtar alla filer som har fil namns tillägget. ps1 som har lagts till eller uppdaterats under den senaste veckan.

Det tredje kommandot använder `Wait-Job` för att vänta tills jobbet är i ett avslutande tillstånd. När jobbet har slutförts visar kommandot jobbobjektet som innehåller information om jobbet.

### Exempel 9: vänta tills jobben har startats på fjärrdatorer genom att använda Invoke-Command

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

Det här exemplet visar hur du använder `Wait-Job` med jobb som har startats på fjärrdatorer med hjälp av parametern **AsJob** i `Invoke-Command` . När du använder **AsJob** skapas jobbet på den lokala datorn och resultaten returneras automatiskt till den lokala datorn, även om jobbet körs på fjärrdatorerna.

I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Process` kommando som körs i sessioner på tre fjärrdatorer är i ett avslutande tillstånd.

Det första kommandot skapar **PSSession** -objekt på tre datorer och lagrar dem i `$s` variabeln.

Det andra kommandot använder `Invoke-Command` för att köra `Get-Process` i var och en av de tre sessionerna i `$s` .
Kommandot använder parametern **AsJob** för att köra kommandot asynkront som ett jobb. Kommandot returnerar ett jobb objekt, precis som de jobb som har startats med hjälp av `Start-Job` , och jobbobjektet lagras i `$j` variabeln.

Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka jobbobjektet till- `$j` `Wait-Job` cmdleten. Ett `Invoke-Command` kommando krävs inte i det här fallet eftersom jobbet finns på den lokala datorn.

### Exempel 10: vänta på ett jobb som har ett ID

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

Det här kommandot väntar på jobbet med ID-värdet 1.

## PARAMETRAR

### – Alla

Anger att denna cmdlet returnerar jobbobjektet och fortsätter körningen när ett jobb har slutförts. Som standard `Wait-Job` väntar det tills alla angivna jobb har slutförts innan meddelandet visas.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Anger en hash-tabell med villkor. Denna cmdlet väntar på jobb som uppfyller alla villkor i hash-tabellen. Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb. Den fungerar inte på standard jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten. Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet fortsätter att vänta på jobb i tillståndet pausad eller frånkopplad. Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:

- Slutförd
- Misslyckad
- Stoppad
- Inaktiverad
- Frånkopplad

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger en matris med ID: n för jobb som denna cmdlet väntar på.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen. Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen. Du kan ange ett eller flera ID: n, avgränsade med kommatecken. Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger en matris med instans-ID: n för jobb som denna cmdlet väntar på. Standardvärdet är alla jobb.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn. Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Jobb

Anger jobb för vilka denna cmdlet väntar. Ange en variabel som innehåller jobb objekt eller ett kommando som hämtar jobb objekt. Du kan också använda en pipeline-operator för att skicka jobb objekt till- `Wait-Job` cmdleten. Som standard `Wait-Job` väntar alla jobb som skapats i den aktuella sessionen.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Anger egna namn på jobb som denna cmdlet väntar på.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Tillstånd

Anger ett jobb tillstånd. Denna cmdlet väntar bara på jobb i det angivna läget. De acceptabla värdena för den här parametern är:

- NotStarted
- Körs
- Slutförd
- Misslyckad
- Stoppad
- Blockerad
- Inaktiverad
- Frånkopplad
- Pausar
- Stoppas

Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

Anger maximal vänte tid för varje jobb, i sekunder. Standardvärdet,-1, anger att cmdleten ska vänta tills jobbet har slutförts. Tids inställningen startar när du skickar `Wait-Job` kommandot, inte `Start-Job` kommandot.

Om den här tiden överskrids fortsätter vänte tiden och körningen även om jobbet fortfarande körs.
Kommandot visar inga fel meddelanden.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. RemotingJob

Du kan skicka vidare ett jobb objekt till denna cmdlet.

## UTDATA

### System. Management. Automation. PSRemotingJob

Denna cmdlet returnerar jobb objekt som representerar jobben i ett avslutande tillstånd. Om vänte tiden slutar eftersom värdet för parametern **timeout** överskrids, `Wait-Job` returnerar inga objekt.

## ANTECKNINGAR

Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:

- Slutförd
- Misslyckad
- Stoppad
- Inaktiverad
- Frånkopplad till direkt om du vill `Wait-Job` fortsätta att vänta på pausade och frånkopplade jobb använder du parametern **Force** .

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)
