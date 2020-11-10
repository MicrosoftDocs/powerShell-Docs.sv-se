---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 28fb50118e3a37aa0ee7b84aac356f7e8b6f2578
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387574"
---
# Get-Job

## SAMMANFATTNING
Hämtar PowerShell-bakgrunds jobb som körs i den aktuella sessionen.

## SYNTAX

### SessionIdParameterSet (standard)

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### NameParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### StateParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## BESKRIVNING

`Get-Job`Cmdleten hämtar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen. Du kan använda `Get-Job` för att hämta jobb som har startats med hjälp av `Start-Job` cmdleten, eller genom att använda parametern **AsJob** för valfri cmdlet.

Utan parametrar hämtar ett- `Get-Job` kommando alla jobb i den aktuella sessionen. Du kan använda parametrarna för `Get-Job` för att hämta specifika jobb.

Jobbobjektet som `Get-Job` returnerar innehåller användbar information om jobbet, men det innehåller inte jobb resultatet. Använd cmdleten för att hämta resultatet `Receive-Job` .

Ett Windows PowerShell-bakgrunds jobb är ett kommando som körs i bakgrunden utan att interagera med den aktuella sessionen. Normalt använder du ett bakgrunds jobb för att köra ett komplicerat kommando som tar lång tid att slutföra. Mer information om bakgrunds jobb i Windows PowerShell finns [about_Jobs](./about/about_Jobs.md).

Från och med Windows PowerShell 3,0 `Get-Job` hämtar cmdlet: en även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb. Om du vill hitta jobb typen för ett jobb använder du jobbets egenskap **PSJobTypeName** .

Om du vill aktivera `Get-Job` en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett `Get-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen. Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.

## EXEMPEL

### Exempel 1: Hämta alla bakgrunds jobb som startats i den aktuella sessionen

Det här kommandot hämtar alla bakgrunds jobb som startats i den aktuella sessionen. Den omfattar inte jobb som skapats i andra sessioner, även om jobben körs på den lokala datorn.

```
PS C:\> Get-Job
```

### Exempel 2: stoppa ett jobb med hjälp av ett instans-ID

De här kommandona visar hur du hämtar instans-ID för ett jobb och sedan använder det för att stoppa ett jobb. Till skillnad från namnet på ett jobb, som inte är unikt, är instans-ID: t unikt.

Det första kommandot använder `Get-Job` cmdleten för att hämta ett jobb. Parametern **Name** används för att identifiera jobbet. Kommandot lagrar jobbobjektet som `Get-Job` returneras i `$j` variabeln. I det här exemplet finns det bara ett jobb med det angivna namnet. Det andra kommandot hämtar **InstanceID** -egenskapen för objektet i `$j` variabeln och lagrar det i `$ID` variabeln. Det tredje kommandot visar värdet för `$ID` variabeln. Det fjärde kommandot använder `Stop-Job` cmdleten för att stoppa jobbet.
Parametern **InstanceID** används för att identifiera jobbet och `$ID` variabeln som representerar JOBBETS instans-ID.

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### Exempel 3: Hämta jobb som innehåller ett speciellt kommando

Det här kommandot hämtar jobben i systemet som innehåller ett `Get-Process` kommando. Kommandot använder **kommando** parametern för `Get-Job` att begränsa de hämtade jobben. Kommandot använder jokertecken ( `*` ) för att hämta jobb som innehåller ett `Get-Process` kommando var som helst i kommando strängen.

```
PS C:\> Get-Job -Command "*get-process*"
```

### Exempel 4: Hämta jobb som innehåller ett speciellt kommando med hjälp av pipelinen

Precis som kommandot i föregående exempel hämtar det här kommandot jobben i systemet som innehåller ett `Get-Process` kommando. Kommandot använder en pipeline-operator ( `|` ) för att skicka en sträng, inom citat tecken, till `Get-Job` cmdlet: en. Det motsvarar föregående kommando.

```
PS C:\> "*get-process*" | Get-Job
```

### Exempel 5: Hämta jobb som inte har startats

Det här kommandot hämtar bara de jobb som har skapats men som ännu inte har startats. Detta inkluderar jobb som är schemalagda att köras i framtiden och som ännu inte har schemalagts.

```
PS C:\> Get-Job -State NotStarted
```

### Exempel 6: Hämta jobb som inte har tilldelats ett namn

Det här kommandot hämtar alla jobb som har jobb namn som börjar med jobbet. Eftersom `job<number>` är standard namnet för ett jobb, hämtar det här kommandot alla jobb som inte har något uttryckligen tilldelat namn.

```
PS C:\> Get-Job -Name Job*
```

### Exempel 7: Använd ett jobb objekt för att representera jobbet i ett kommando

Det här exemplet visar hur du använder `Get-Job` för att hämta ett jobb objekt, och sedan visar det hur du använder jobbobjektet för att representera jobbet i ett kommando.

Det första kommandot använder `Start-Job` cmdleten för att starta ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn. Kommandot använder **Name** -parametern för `Start-Job` att tilldela jobbet ett eget namn. Det andra kommandot använder `Get-Job` för att hämta jobbet. Den använder **Name** -parametern för `Get-Job` att identifiera jobbet. Kommandot sparar det resulterande jobbobjektet i `$j` variabeln. Det tredje kommandot visar värdet för jobbobjektet i `$j` variabeln. Värdet för egenskapen **State** visar att jobbet har slutförts. Värdet för egenskapen **HasMoreData** visar att det finns resultat som är tillgängliga från jobbet som ännu inte har hämtats. Det fjärde kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet. Objektet används i `$j` variabeln för att representera jobbet. Du kan också använda en pipeline-operator för att skicka ett jobb objekt till `Receive-Job` .

```
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob
PS C:\> $j = Get-Job -Name MyJob
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```


### Exempel 8: Hämta alla jobb inklusive jobb som har startats med en annan metod

Det här exemplet visar att `Get-Job` cmdleten kan hämta alla jobb som startades i den aktuella sessionen, även om de startades med hjälp av olika metoder.

Det första kommandot använder `Start-Job` cmdleten för att starta ett jobb på den lokala datorn. Det andra kommandot använder **AsJob** -parametern för `Invoke-Command` cmdleten för att starta ett jobb på S1-datorn. Även om kommandona i jobbet körs på fjärrdatorn skapas jobbobjektet på den lokala datorn, så du kan använda lokala kommandon för att hantera jobbet. Det tredje kommandot använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på S2-datorn. Med den här metoden skapas jobbobjektet på fjärrdatorn, så du kan använda fjärrkommandon för att hantera jobbet. Det fjärde kommandot använder `Get-Job` för att hämta jobb som lagras på den lokala datorn. Egenskapen **PSJobTypeName** för jobb, som introducerades i Windows PowerShell 3,0, visar att det lokala jobbet som startades med hjälp av `Start-Job` cmdleten är ett bakgrunds jobb och att jobbet startade i en fjärrsession med hjälp av `Invoke-Command` cmdleten är ett Fjärrjobb. Det femte kommandot använder `Invoke-Command` för att köra ett `Get-Job` kommando på S2-datorn. Exempel resultatet visar resultatet av `Get-Job` kommandot. På S2-datorn verkar jobbet vara ett lokalt jobb. Dator namnet är localhost och jobb typen är ett bakgrunds jobb. Mer information om hur du kör bakgrunds jobb på fjärrdatorer finns [about_Remote_Jobs](./about/about_Remote_Jobs.md).

```
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

### Exempel 9: Undersök ett misslyckat jobb

Det här kommandot visar hur du använder jobbobjektet som `Get-Job` returnerar för att undersöka varför ett jobb har misslyckats.
Det visar också hur du hämtar de underordnade jobben för varje jobb.

Det första kommandot använder `Start-Job` cmdleten för att starta ett jobb på den lokala datorn. Jobbobjektet som `Start-Job` returnerar visar att jobbet misslyckades. Det gick inte att **Ange värdet för tillstånds** egenskapen.

Det andra kommandot använder `Get-Job` cmdleten för att hämta jobbet. Kommandot använder punkt metoden för att hämta värdet för objektets **JobStateInfo** -egenskap. Den använder en pipeline-operator för att skicka objektet i egenskapen **JobStateInfo** till `Format-List` cmdleten, som formaterar alla egenskaper för objektet ( `*` ) i en lista. Resultatet av `Format-List` kommandot visar att värdet för jobbets **orsaks** egenskap är tomt.

Det tredje kommandot undersöker mer. Det använder ett `Get-Job` kommando för att hämta jobbet och använder sedan en pipeline-operator för att skicka hela jobbobjektet till `Format-List` cmdleten, som visar alla egenskaper för jobbet i en lista. Visningen av alla egenskaper i jobbobjektet visar att jobbet innehåller ett underordnat jobb med namnet Job2.

Det fjärde kommandot använder `Get-Job` för att hämta jobbobjektet som representerar det underordnade Job2-jobbet. Det här är det jobb där kommandot faktiskt kördes. Metoden dot används för att hämta egenskapen **orsak** för egenskapen **JobStateInfo** . Resultatet visar att jobbet misslyckades på grund av ett nekat åtkomst fel. I det här fallet har användaren glömt att använda alternativet Kör som administratör när Windows PowerShell startades. eftersom bakgrunds jobb använder funktionerna för fjärr kommunikation i Windows PowerShell måste datorn konfigureras för fjärr kommunikation för att köra ett jobb, även när jobbet körs på den lokala datorn. Information om krav för fjärr kommunikation i Windows PowerShell finns [about_Remote_Requirements](./about/about_Remote_Requirements.md). Fel söknings tips finns i [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).

```
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the
following error message: Access is denied.
```

### Exempel 10: hämta filtrerade resultat

Det här exemplet visar hur du använder **filter** parametern för att hämta ett arbets flödes jobb. **Filter** parametern, som introducerades i Windows PowerShell 3,0, är bara giltig för anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.

Det första kommandot använder **arbets flödets** nyckelord för att skapa WFProcess-arbetsflödet. Det andra kommandot använder parametern **AsJob** i WFProcess-arbetsflödet för att köra arbets flödet som ett bakgrunds jobb. Den använder parametern **JobName** i arbets flödet för att ange ett namn för jobbet och parametern **PSPrivateMetadata** för arbets flödet för att ange ett anpassat ID. Det tredje kommandot använder **filter** parametern för `Get-Job` för att hämta jobbet efter anpassat ID som angavs i parametern **PSPrivateMetadata** .

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### Exempel 11: Hämta information om underordnade jobb

I det här exemplet visas effekterna av att använda parametrarna **IncludeChildJob** och **ChildJobState** för `Get-Job` cmdleten.

Det första kommandot hämtar jobben i den aktuella sessionen. Utdata innehåller ett bakgrunds jobb, ett Fjärrjobb och flera instanser av ett schemalagt jobb. Fjärrjobbet, Job4, verkar ha misslyckats.
Det andra kommandot använder parametern **IncludeChildJob** i `Get-Job` . Utdata lägger till de underordnade jobben för alla jobb som har underordnade jobb. I det här fallet visar den ändrade utmatningen att endast det Job5 underordnade jobbet för Job4 misslyckades. Det tredje kommandot använder parametern **ChildJobState** med värdet misslyckades. utdata innehåller alla överordnade jobb och endast de underordnade jobb som misslyckades. Det femte kommandot använder egenskapen **JobStateInfo** för jobb och dess **orsaks** egenskap för att upptäcka varför Job5 misslyckades.

```
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
```

Mer information finns i hjälp avsnittet för [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) .

## PARAMETRAR

### – Efter

Hämtar slutförda jobb som avslutas efter angivet datum och tid. Ange ett **datetime** -objekt, till exempel ett som returneras av `Get-Date` cmdleten eller en sträng som kan konverteras till ett **datetime** -objekt, till exempel `Dec 1, 2012 2:00 AM` eller `11/06` .

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap. Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten. Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Före

Hämtar slutförda jobb som slutade före det angivna datumet och den angivna tiden. Ange ett **datetime** -objekt.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap. Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten. Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

Hämtar endast de underordnade jobb som har det angivna läget. De acceptabla värdena för den här parametern är:

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

Som standard `Get-Job` får inte underordnade jobb. Med hjälp av parametern **IncludeChildJob** `Get-Job` hämtar du alla underordnade jobb. Om du använder parametern **ChildJobState** har parametern **IncludeChildJob** ingen påverkan.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kommando

Anger en matris med kommandon som strängar. Denna cmdlet hämtar de jobb som innehåller de angivna kommandona. Standardvärdet är alla jobb. Du kan använda jokertecken för att ange ett kommando mönster.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Filter

Anger en hash-tabell med villkor. Denna cmdlet hämtar jobb som uppfyller alla villkor.
Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb. Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten. Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

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

### -HasMoreData

Indikerar om denna cmdlet endast hämtar jobb som har angivet värde för egenskapen **HasMoreData** .
Egenskapen **HasMoreData** anger om alla jobb resultat har tagits emot i den aktuella sessionen. Ange ett värde för om du vill hämta jobb som har fler resultat `$True` . Ange ett värde för om du vill hämta jobb som inte har fler resultat `$False` .

Använd cmdleten för att hämta resultatet av ett jobb `Receive-Job` .

När du använder `Receive-Job` cmdleten tas den bort från dess minnes intern, sessionsbaserade lagrings utrymme som returneras. När det har returnerat alla resultat från jobbet i den aktuella sessionen anges värdet för **HasMoreData** -egenskapen för jobbet till `$False` ) för att indikera att det inte har några fler resultat för jobbet i den aktuella sessionen. Använd parametern **Behåll** för `Receive-Job` att förhindra `Receive-Job` borttagning av resultat och ändra värdet för egenskapen **HasMoreData** .
För mer information ange `Get-Help Receive-Job`.

Egenskapen **HasMoreData** är unik för den aktuella sessionen. Om resultat för en anpassad Jobbtyp sparas utanför sessionen, till exempel den schemalagda jobbtyp som sparar jobb resultat på disk, kan du använda `Receive-Job` cmdleten i en annan session för att hämta jobb resultatet igen, även om värdet för **HasMoreData** är `$False` . Mer information finns i hjälp avsnitten för den anpassade jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger en matris med ID: n för jobb som denna cmdlet hämtar.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen. Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen. Du kan ange ett eller flera ID: n avgränsade med kommatecken. Om du vill hitta ID: t för ett jobb skriver du `Get-Job` utan parametrar.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeChildJob

Anger att den här cmdleten Returnerar underordnade jobb, förutom överordnade jobb.

Den här parametern är särskilt användbar för att undersöka arbets flödes jobb, som `Get-Job` returnerar ett överordnat jobb och jobb haveri, eftersom orsaken till felet har sparats i en egenskap för det underordnade jobbet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Anger en matris med instans-ID för jobb som denna cmdlet hämtar. Standardvärdet är alla jobb.

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

### -Name

Anger en matris med informativa namn på jobb som denna cmdlet hämtar. Ange ett jobbnamn eller Använd jokertecken för att ange ett jobb namns mönster. Som standard `Get-Job` hämtar alla jobb i den aktuella sessionen.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Nyaste

Anger ett antal jobb som ska hämtas. Denna cmdlet hämtar de jobb som avslutades senast.

Den **senaste** parametern kan inte sortera eller returnera de senaste jobben i slut tid. Använd cmdleten för att sortera utdata `Sort-Object` .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tillstånd

Anger ett jobb tillstånd. Denna cmdlet hämtar endast jobb i det angivna läget. De acceptabla värdena för den här parametern är:

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

Som standard `Get-Job` hämtar alla jobb i den aktuella sessionen.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. RemotingJob

Denna cmdlet returnerar objekt som representerar jobben i sessionen.

## ANTECKNINGAR

**PSJobTypeName** -egenskapen för jobb anger jobb typen för jobbet. Egenskap svärdet bestäms av jobb typ författaren. I följande lista visas vanliga jobb typer.

- **BackgroundJob**. Lokalt jobb har startats med hjälp av `Start-Job` .
- **RemoteJob**. Jobbet startade i en **PSSession** med hjälp av parametern **AsJob** för `Invoke-Command` cmdleten.
- **PSWorkflowJob**. Jobbet startades med **AsJob** gemensamma parameter för arbets flöden.

## RELATERADE LÄNKAR

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)
