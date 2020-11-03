---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: b69688891df70c396d19911624c58ae7733183d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264087"
---
# Wait-Job

## SAMMANFATTNING
Ignorerar kommando tolken tills en eller flera av PowerShell-bakgrunds jobben som körs i sessionen har slutförts.

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

Cmdleten **wait-Job** väntar på att PowerShell-arbetsjobben ska slutföras innan kommando tolken visas.
Du kan vänta tills ett bakgrunds jobb har slutförts, eller tills alla bakgrunds jobb är slutförda, och du kan ange en maximal vänte tid för jobbet.

När kommandona i jobbet är slutförda visar **vänta-jobb** kommando tolken och returnerar ett Job-objekt så att du kan skicka vidare till ett annat kommando.

Du kan använda cmdleten **wait-Job** för att vänta på bakgrunds jobb, till exempel de som startades med hjälp av Start-Job-cmdlet eller parametern *AsJob* i Invoke-Command-cmdleten.
Mer information om PowerShell-bakgrunds jobb finns about_Jobs.

Från och med Windows PowerShell 3,0 väntar **väntande jobb-** cmdleten på anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.
Om du vill att **vänta – jobb** ska vänta på jobb av en viss typ importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör Get-Job-cmdlet, antingen genom att använda cmdleten Import-Module eller genom att använda eller hämta en cmdlet i modulen.
Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.

## EXEMPEL

### Exempel 1: vänta på alla jobb

```powershell
Get-Job | Wait-Job
```

Det här kommandot väntar på att alla bakgrunds jobb som körs i sessionen ska slutföras.

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

Det här exemplet visar hur du använder cmdleten **wait-Job** med jobb som har startats på fjärrdatorer med hjälp av cmdleten **Start-Job** .
Både **Start-** och **wait-Job-** kommandon skickas till fjärrdatorn med hjälp av cmdleten **Invoke-Command** .

I det här exemplet används **wait-Job** för att avgöra om ett Get-Date kommando som körs som ett bakgrunds jobb på tre olika datorer är klart.

Det första kommandot skapar en PowerShell-session ( **PSSession** ) på var och en av de tre fjärrdatorerna och lagrar dem i $s-variabeln.

Det andra kommandot använder **Invoke-Command** för att köra **Start jobb** i var och en av de tre sessionerna i $s.
Alla jobb har namnet datum1.

Det tredje kommandot använder **Invoke-Command** för att köra **wait-Job**.
Det här kommandot väntar på att datum1-jobben på varje dator ska slutföras.
Den innehåller den resulterande samlingen (matris) av jobb objekt i variabeln $done.

Det fjärde kommandot använder egenskapen **Count** i matrisen med jobb objekt i variabeln $Done för att fastställa hur många av jobben som är klara.

### Exempel 3: Bestäm när det första bakgrunds jobbet slutförs

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

I det här exemplet används *alla* parametrar för **vänta-jobb** för att fastställa när den första av många bakgrunds jobb som körs i den aktuella sessionen har slutförts.
Det visar också hur du använder cmdleten **wait-Job** för att vänta på att fjärrjobben ska slutföras.

Det första kommandot skapar en **PSSession** på varje dator som anges i Machines.txt-filen och lagrar **PSSession** -objekten i $s-variabeln.
Kommandot använder cmdleten Get-Content för att hämta innehållet i filen.
Kommandot **Get-Content** omges av parenteser för att kontrol lera att det körs före kommandot New-PSSession.

Det andra kommandot lagrar en kommando sträng för **Get-EventLog** , inom citat tecken, i variabeln $c.

Det tredje kommandot använder Invoke-Command cmdlet för att köra **Start jobb** i varje session i $s.
Kommandot **Start-Job** startar ett bakgrunds jobb som kör kommandot **Get-EventLog** i $c-variabeln.

Kommandot **använder omfångs** modifieraren för att indikera att variabeln $c definierades på den lokala datorn.
Omfångs modifieraren **använder** introduceras i Windows PowerShell 3,0.
Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](about/about_Remote_Variables.md).

Det fjärde kommandot använder **Invoke-Command** för att köra ett **wait-Job-** kommando i sessionerna.
Den använder *valfri* parameter för att vänta tills det första jobbet på fjärrdatorerna har slutförts.

### Exempel 4: Ange en vänte tid för jobb på fjärrdatorer

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

Det här exemplet visar hur du använder *timeout* -parametern för **wait-Job** för att ange en maximal vänte tid för de jobb som körs på fjärrdatorer.

Det första kommandot skapar en **PSSession** på var och en av de tre fjärrdatorerna (Server01, Server02 och Server03) och lagrar sedan **PSSession** -objekten i $s-variabeln.

Det andra kommandot använder **Invoke-Command** för att köra **Start-Job** i vart och ett av **PSSession** -objekten i $s.
Den lagrar de resulterande jobb objekten i variabeln $jobs.

Det tredje kommandot använder **Invoke-Command** för att köra **wait-Job** i varje session i $s.
Kommandot **wait-Job** avgör om alla kommandon har slutförts inom 30 sekunder.
Den använder parametern *timeout* med ett värde på 30 för att fastställa den maximala vänte tiden och lagrar sedan kommandots resultat i variabeln $Done.

I det här fallet är det bara kommandot på Server02-datorn som har slutförts efter 30 sekunder.
**Vänta – jobbet** slutar vänta, visar kommando tolken och returnerar objektet som representerar det jobb som har slutförts.

Variabeln $done innehåller ett jobb objekt som representerar jobbet som kördes på Server02.

### Exempel 5: vänta tills ett av flera jobb har slutförts

```powershell
Wait-Job -id 1,2,5 -Any
```

Detta kommando identifierar tre jobb efter deras ID och väntar tills någon av dem har slutförts.
Kommando tolken returnerar när det första jobbet har slutförts.

### Exempel 6: vänta i en period och Tillåt sedan att jobbet fortsätter i bakgrunden

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

Det här kommandot väntar 120 sekunder (två minuter) för att DailyLog-jobbet ska slutföras.
Om jobbet inte slutförs inom de kommande två minuterna returnerar kommando tolken ändå och jobbet fortsätter att köras i bakgrunden.

### Exempel 7: vänta på ett jobb efter namn

```powershell
Wait-Job -Name "Job3"
```

Det här kommandot använder jobb namnet för att identifiera det jobb som ska vänta.

### Exempel 8: vänta tills jobb på den lokala datorn har startats med Start-Job

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

Det här exemplet visar hur du använder cmdleten **wait-Job** med jobb som har startats på den lokala datorn med hjälp av **Start-Job**.

Kommandona startar ett jobb som hämtar PowerShell-skriptfilerna som har lagts till eller uppdaterats under den senaste veckan.

Det första kommandot använder **Start-Job** för att starta ett bakgrunds jobb på den lokala datorn.
Jobbet kör ett Get-ChildItem-kommando som hämtar alla filer som har fil namns tillägget. ps1 som har lagts till eller uppdaterats under den senaste veckan.

Det tredje kommandot använder **wait-Job** för att vänta tills jobbet har slutförts.
När jobbet har slutförts visar kommandot jobbobjektet som innehåller information om jobbet.

### Exempel 9: vänta tills jobben har startats på fjärrdatorer genom att använda Invoke-Command

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

Det här exemplet visar hur du använder **wait-Job** med jobb som har startats på fjärrdatorer med hjälp av parametern *AsJob* för **Invoke-Command**.
När du använder *AsJob* skapas jobbet på den lokala datorn och resultaten returneras automatiskt till den lokala datorn, även om jobbet körs på fjärrdatorerna.

I det här exemplet används **wait-Job** för att avgöra om ett **Get-process-** kommando som körs i sessionerna på tre fjärrdatorer har slutförts.

Det första kommandot skapar **PSSession** -objekt på tre datorer och lagrar dem i $s-variabeln.

Det andra kommandot använder **Invoke-Command** för att köra **Get-process** i var och en av de tre sessionerna i $s.
Kommandot använder parametern *AsJob* för att köra kommandot asynkront som ett bakgrunds jobb.
Kommandot returnerar ett jobb objekt, precis som de jobb som startas med hjälp av **Start-Job** , och jobbobjektet lagras i $j variabeln.

Det tredje kommandot använder en pipeline-operator (|) för att skicka jobbobjektet i $j till cmdleten **wait-Job** .
Ett **Invoke-kommando-** kommando krävs inte i det här fallet eftersom jobbet finns på den lokala datorn.

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

Anger att denna cmdlet visar kommando tolken och returnerar jobbobjektet när ett jobb har slutförts.
Som standard väntar **jobbet** tills alla angivna jobb är slutförda innan meddelandet visas.

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

Anger en hash-tabell med villkor.
Denna cmdlet väntar på jobb som uppfyller alla villkor i hash-tabellen.
Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.
Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .
Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

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

Anger att denna cmdlet fortsätter att vänta på jobb i tillståndet pausad eller frånkopplad.
Som standard returnerar **wait-jobb** eller avslutar vänte läge när jobben är i något av följande tillstånd:

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

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.
Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.
Du kan ange ett eller flera ID: n, avgränsade med kommatecken.
Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .

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

Anger en matris med instans-ID: n för jobb som denna cmdlet väntar på.
Standardvärdet är alla jobb.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.
Använd **Get-Job** för att hitta instans-ID för ett jobb.

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

Anger jobb för vilka denna cmdlet väntar.
Ange en variabel som innehåller jobb objekt eller ett kommando som hämtar jobb objekt.
Du kan också använda en pipeline-operator för att skicka jobb objekt till cmdleten **wait-Job** .
Som standard väntar **jobbet** på alla jobb som skapats i den aktuella sessionen.

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

Anger ett jobb tillstånd.
Denna cmdlet väntar bara på jobb i det angivna läget.
De acceptabla värdena för den här parametern är:

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

Mer information om jobb tillstånd finns i [JobState-uppräkning](https://msdn.microsoft.com/library/system.management.automation.jobstate) i MSDN-biblioteket.

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

Anger maximal vänte tid för varje bakgrunds jobb, i sekunder.
Standardvärdet,-1, anger att cmdleten ska vänta tills jobbet har slutförts.
Tids inställningen startar när du skickar kommandot **vänta – jobb** , inte kommandot **Start-Job** .

Om den här tiden överskrids, avslutas vänte tiden och kommando tolken returnerar, även om jobbet fortfarande körs.
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

Denna cmdlet returnerar jobb objekt som representerar de slutförda jobben.
Om vänte tiden slutar på grund av att värdet för *timeout* -parametern har överskridits, returnerar inte **väntande jobb** några objekt.

## ANTECKNINGAR

* Som standard returnerar **wait-jobb** eller avslutar vänte läge när jobben är i något av följande tillstånd:

- Slutförd
- Misslyckad
- Stoppad
- Inaktiverad
- Frånkopplad till direkt **vänte läge** om du vill fortsätta vänta på pausade och frånkopplade jobb använder du parametern *Force* .

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

