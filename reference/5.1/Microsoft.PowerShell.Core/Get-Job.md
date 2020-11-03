---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263613"
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

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
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

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Get-Job** hämtar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.
Du kan använda **Get-Job** för att hämta jobb som har startats med hjälp av Start-Job-cmdlet, eller genom att använda parametern *AsJob* för valfri cmdlet.

Utan parametrar hämtar kommandot **Get-Job** alla jobb i den aktuella sessionen.
Du kan använda parametrarna för **Get-Job** för att hämta specifika jobb.

Jobbobjektet som returnerar jobb innehåller användbar information **om jobbet,** men det innehåller inte jobb resultatet.
Använd Receive-Job-cmdleten för att hämta resultatet.

Ett Windows PowerShell-bakgrunds jobb är ett kommando som körs i bakgrunden utan att interagera med den aktuella sessionen.
Normalt använder du ett bakgrunds jobb för att köra ett komplicerat kommando som tar lång tid att slutföra.
Mer information om bakgrunds jobb i Windows PowerShell finns about_Jobs.

Från och med Windows PowerShell 3,0 hämtar cmdleten **Get-Job** även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.
Om du vill hitta jobb typen för ett jobb använder du jobbets egenskap **PSJobTypeName** .

Om du vill aktivera **Get-Job** för att hämta en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör kommandot **Get-Job** , antingen genom att använda Import-Module cmdlet eller genom att använda eller hämta en cmdlet i modulen.
Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.

## EXEMPEL

### Exempel 1: Hämta alla bakgrunds jobb som startats i den aktuella sessionen

```
PS C:\> Get-Job
```

Det här kommandot hämtar alla bakgrunds jobb som startats i den aktuella sessionen.
Den omfattar inte jobb som skapats i andra sessioner, även om jobben körs på den lokala datorn.

### Exempel 2: stoppa ett jobb med hjälp av ett instans-ID

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

De här kommandona visar hur du hämtar instans-ID för ett jobb och sedan använder det för att stoppa ett jobb.
Till skillnad från namnet på ett jobb, som inte är unikt, är instans-ID: t unikt.

### Exempel 3: Hämta jobb som innehåller ett speciellt kommando

```
PS C:\> Get-Job -Command "*get-process*"
```

Det här kommandot hämtar jobben på systemet som innehåller ett Get-Process-kommando.
Kommandot använder *kommando* parametern för **Get-Job** för att begränsa de jobb som hämtas.
Kommandot använder jokertecken (*) för att hämta jobb som innehåller kommandot **Get-process** var som helst i kommando strängen.

### Exempel 4: Hämta jobb som innehåller ett speciellt kommando med hjälp av pipelinen

```
PS C:\> "*get-process*" | Get-Job
```

Precis som kommandot i föregående exempel hämtar det här kommandot jobben i systemet som innehåller kommandot **Get-process** .
Kommandot använder en pipeline-operator (|) för att skicka en sträng, inom citat tecken, till cmdleten **Get-Job** .
Det motsvarar föregående kommando.

### Exempel 5: Hämta jobb som inte har startats

```
PS C:\> Get-Job -State NotStarted
```

Det här kommandot hämtar bara de jobb som har skapats men som ännu inte har startats.
Detta inkluderar jobb som är schemalagda att köras i framtiden och som ännu inte har schemalagts.

### Exempel 6: Hämta jobb som inte har tilldelats ett namn

```
PS C:\> Get-Job -Name Job*
```

Det här kommandot hämtar alla jobb som har jobb namn som börjar med jobbet.
Eftersom jobbet \<number\> är standard namnet för ett jobb, hämtar det här kommandot alla jobb som inte har något uttryckligen tilldelat namn.

### Exempel 7: Använd ett jobb objekt för att representera jobbet i ett kommando

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

Det här exemplet visar hur du använder **Get-Job** för att hämta ett jobb objekt, och sedan visar det hur du använder jobbobjektet för att representera jobbet i ett kommando.

### Exempel 8: Hämta alla jobb inklusive jobb som har startats med en annan metod

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

Det här exemplet visar att cmdleten **Get-Job** kan hämta alla jobb som startades i den aktuella sessionen, även om de startades med hjälp av olika metoder.

### Exempel 9: Undersök ett misslyckat jobb

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
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

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

Det här kommandot visar hur du använder jobbobjektet som **Get-Job-** returer för att undersöka varför ett jobb har misslyckats.
Det visar också hur du hämtar de underordnade jobben för varje jobb.

### Exempel 10: hämta filtrerade resultat

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

Det här exemplet visar hur du använder *filter* parametern för att hämta ett arbets flödes jobb.
*Filter* parametern, som introducerades i Windows PowerShell 3,0, är bara giltig för anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.

### Exempel 11: Hämta information om underordnade jobb

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
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

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
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

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

I det här exemplet visas effekterna av att använda parametrarna *IncludeChildJob* och *ChildJobState* för **Get-Job-** cmdleten.

## PARAMETRAR

### – Efter

Hämtar slutförda jobb som avslutas efter angivet datum och tid.
Ange ett **datetime** -objekt, till exempel ett som returneras av Get-Date-cmdlet eller en sträng som kan konverteras till ett **datetime** -objekt, till exempel `Dec 1, 2012 2:00 AM` eller `11/06` .

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.
Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .
Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Före

Hämtar slutförda jobb som slutade före det angivna datumet och den angivna tiden.
Ange ett **datetime** -objekt.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.
Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .
Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

Hämtar endast de underordnade jobb som har det angivna läget.
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

Som standard får **Get-Job** inte underordnade jobb.
Genom att använda *IncludeChildJob* -parametern hämtar **Get-Job** alla underordnade jobb.
Om du använder parametern *ChildJobState* har parametern *IncludeChildJob* ingen påverkan.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kommando

Anger en matris med kommandon som strängar.
Denna cmdlet hämtar de jobb som innehåller de angivna kommandona.
Standardvärdet är alla jobb.
Du kan använda jokertecken för att ange ett kommando mönster.

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

Anger en hash-tabell med villkor.
Denna cmdlet hämtar jobb som uppfyller alla villkor.
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

### -HasMoreData

Indikerar om denna cmdlet endast hämtar jobb som har angivet värde för egenskapen **HasMoreData** .
Egenskapen **HasMoreData** anger om alla jobb resultat har tagits emot i den aktuella sessionen.
Ange ett värde för $True för att hämta jobb som har fler resultat.
Ange ett värde för $False om du vill hämta jobb som inte har fler resultat.

Om du vill hämta resultatet av ett jobb använder du cmdleten Receive-Job.

När du använder cmdleten **Receive-Job** , tas den bort från dess minnes intern, sessionsbaserade lagrings utrymme som returneras.
När det har returnerat alla resultat från jobbet i den aktuella sessionen anges värdet för **HasMoreData** -egenskapen för jobbet till $false) för att indikera att det inte har några fler resultat för jobbet i den aktuella sessionen.
Använd parametern *Behåll* för **Receive-Job** för att förhindra **mottagning – jobb** från att ta bort resultat och ändra värdet för egenskapen **HasMoreData** .
För mer information ange `Get-Help Receive-Job`.

Egenskapen **HasMoreData** är unik för den aktuella sessionen.
Om resultat för en anpassad Jobbtyp sparas utanför sessionen, till exempel den schemalagda jobbtyp som sparar jobb resultat på disk, kan du använda cmdleten **Receive-Job** i en annan session för att hämta jobb resultatet igen, även om värdet för **HasMoreData** är $false.
Mer information finns i hjälp avsnitten för den anpassade jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger en matris med ID: n för jobb som denna cmdlet hämtar.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.
Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.
Du kan ange ett eller flera ID: n avgränsade med kommatecken.
Om du vill hitta ID: t för ett jobb skriver du `Get-Job` utan parametrar.

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

Den här parametern är särskilt användbar för att undersöka arbets flödes jobb, för vilka **Get-Job** returnerar ett överordnat behållar jobb och jobb haverier, eftersom orsaken till felet har sparats i en egenskap för det underordnade jobbet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Anger en matris med instans-ID för jobb som denna cmdlet hämtar.
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

### -Name

Anger en matris med informativa namn på jobb som denna cmdlet hämtar.
Ange ett jobbnamn eller Använd jokertecken för att ange ett jobb namns mönster.
Som standard hämtar **Get-Job** alla jobb i den aktuella sessionen.

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

Anger ett antal jobb som ska hämtas.
Denna cmdlet hämtar de jobb som avslutades senast.

Den *senaste* parametern kan inte sortera eller returnera de senaste jobben i slut tid.
Om du vill sortera utdata använder du Sort-Object cmdlet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tillstånd

Anger ett jobb tillstånd.
Denna cmdlet hämtar endast jobb i det angivna läget.
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

Som standard hämtar **Get-Job** alla jobb i den aktuella sessionen.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. RemotingJob

Denna cmdlet returnerar objekt som representerar jobben i sessionen.

## ANTECKNINGAR

* **PSJobTypeName** -egenskapen för jobb anger jobb typen för jobbet. Egenskap svärdet bestäms av jobb typ författaren. I följande lista visas vanliga jobb typer.

  - **BackgroundJob**.
Ett lokalt jobb har startats med hjälp av **Start-Job**.

  - **RemoteJob**.
Jobbet startades i en **PSSession** med hjälp av parametern *AsJob* i Invoke-Command-cmdleten.

  - **PSWorkflowJob**.
Jobbet startades med *AsJob* gemensamma parameter för arbets flöden.

## RELATERADE LÄNKAR

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Återuppta – jobb](Resume-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Pausa – jobb](Suspend-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)
