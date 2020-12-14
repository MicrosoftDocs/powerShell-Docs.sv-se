---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710483"
---
# Receive-Job

## SAMMANFATTNING
Hämtar resultatet av PowerShell-bakgrunds jobben i den aktuella sessionen.

## SYNTAX

### Plats (standard)

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### ComputerName

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### Session

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### NameParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### SessionIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## BESKRIVNING

`Receive-Job`Cmdlet: en hämtar resultatet av PowerShell bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för valfri cmdlet.
Du kan få resultaten av alla jobb eller identifiera jobb efter namn, ID, instans-ID, dator namn, plats eller session eller genom att skicka ett jobb objekt.

När du startar ett PowerShell-bakgrunds jobb startar jobbet, men resultaten visas inte direkt. I stället returnerar kommandot ett objekt som representerar bakgrunds jobbet.
Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte resultatet.
Med den här metoden kan du fortsätta att arbeta i sessionen medan jobbet körs.
Mer information om bakgrunds jobb i PowerShell finns [about_Jobs](./About/about_Jobs.md).

`Receive-Job`Cmdlet: en hämtar de resultat som har genererats vid den tidpunkt då `Receive-Job` kommandot skickas.
Om resultatet inte har slutförts ännu kan du köra ytterligare `Receive-Job` kommandon för att få återstående resultat.

Som standard tas jobb resultaten bort från systemet när du tar emot dem, men du kan använda parametern **Keep** för att spara resultaten så att du kan ta emot dem igen.
Om du vill ta bort jobb resultaten kör du `Receive-Job` kommandot igen utan parametern **Keep** , stänger sessionen eller använder `Remove-Job` cmdleten för att ta bort jobbet från sessionen.

Från och med Windows PowerShell 3,0 `Receive-Job` får även resultaten av anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.
Om du vill göra `Receive-Job` det möjligt att hämta resultatet av en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan den kör ett `Receive-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.
Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.

## EXEMPEL

### Exempel 1: få resultat för ett visst jobb

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

Dessa kommandon använder **jobb** parametern för `Receive-Job` för att hämta resultatet av ett visst jobb.

Det första kommandot startar ett jobb med `Start-Job` och lagrar jobbobjektet i `$job` variabeln.

Det andra kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.
Den använder **jobb** parametern för att ange jobbet.

### Exempel 2: Använd parametern Keep

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

I det här exemplet lagras ett jobb i `$job` variabeln och det rör sig om jobbet till `Receive-Job` cmdleten. `-Keep`Parametern används också för att tillåta att alla sammanställda data ström data hämtas igen efter den första vyn.

### Exempel 3: få resultat från flera bakgrunds jobb

När du använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb skapas jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorerna.
Därför använder du lokala kommandon för att hantera jobbet.

När du använder **AsJob** returnerar PowerShell dessutom ett jobb objekt som innehåller ett underordnat jobb för varje jobb som startades. I det här fallet innehåller jobbobjektet tre underordnade jobb, ett för varje jobb på varje fjärrdator.

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### Exempel 4: få resultat från bakgrunds jobb på flera fjärrdatorer

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

I det här exemplet visas hur du får resultaten av bakgrunds jobb som körs på tre fjärrdatorer.
Till skillnad från föregående exempel, `Invoke-Command` som använder för att köra `Start-Job` kommandot, startade de tre oberoende jobben på var och en av de tre datorerna. Därför returnerade kommandot tre jobb objekt som representerar tre jobb som körs lokalt på tre olika datorer.

> [!NOTE]
> I det sista kommandot, eftersom `$j` är en lokal variabel, använder-skript blocket **using** scope modifierare för att identifiera `$j` variabeln. Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./About/about_Remote_Variables.md).

### Exempel 5: åtkomst till underordnade jobb

`-Keep`Parametern bevarar statusen för de aggregerade strömmarna för ett jobb så att det kan visas igen. Utan den här parametern raderas alla aggregerade data ström data när jobbet tas emot. Mer information finns i [about_Job_Details](About/about_Job_Details.md#child-jobs)

> [!NOTE]
> De aggregerade strömmarna inkluderar strömmarna för alla underordnade jobb. Du kan fortfarande komma åt de enskilda data strömmarna via jobbobjektet och underordnade jobb objekt.

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## PARAMETRAR

### -AutoRemoveJob

Anger att den här cmdleten tar bort jobbet när det har returnerat jobb resultatet.
Om jobbet har fler resultat tas jobbet fortfarande bort, men `Receive-Job` visar ett meddelande.

Den här parametern fungerar bara på anpassade jobb typer.
Den är utformad för instanser av jobb typer som sparar jobbet eller typen utanför sessionen, till exempel instanser av schemalagda jobb.

Den här parametern kan inte användas utan parametern **wait** .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger en matris med namn på datorer.

Den här parametern väljs bland de jobb resultat som lagras på den lokala datorn.
Den hämtar inte data för jobb som körs på fjärrdatorer.
Om du vill hämta jobb resultat som lagras på fjärrdatorer använder du `Invoke-Command` cmdleten för att fjärrköra ett `Receive-Job` kommando.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Force

Anger att denna cmdlet fortsätter att vänta om jobb är i tillståndet **Suspended** eller **disconnectd** . Som standard returnerar **wait** -parametern i `Receive-Job` returnerar eller avbryter vänte tiden när jobben är i något av följande tillstånd:

- Slutförd
- Misslyckad
- Stoppad
- Inaktiverad
- Frånkopplad.

Parametern **Force** är giltig endast om parametern **wait** också används i kommandot.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger en matris med ID: n.
Den här cmdleten hämtar resultatet av jobb med de angivna ID: na.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.
Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen. Du kan ange ett eller flera ID: n avgränsade med kommatecken.
Använd om du vill hitta ID: t för ett jobb `Get-Job` .

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

Anger en matris med instans-ID: n.
Den här cmdleten hämtar resultatet av jobb med de angivna instans-ID: na.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.
Använd cmdleten för att hitta instans-ID för ett jobb `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Jobb

Anger det jobb för vilket resultat hämtas.

Ange en variabel som innehåller jobbet eller ett kommando som hämtar jobbet.
Du kan också skicka ett jobb objekt till `Receive-Job` .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Behåll

Anger att denna cmdlet sparar de aggregerade data strömmarna i systemet, även efter att du har tagit emot dem. Som standard raderas aggregerade data ström data efter att de har visats med `Receive-Job` .

Om du stänger sessionen eller tar bort jobbet med `Remove-Job` cmdleten raderas även sammanställda data ström data.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Plats

Anger en matris med platser.
Denna cmdlet hämtar bara resultatet av jobb på de angivna platserna.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger en matris med användarvänliga namn.
Den här cmdleten hämtar resultatet av jobb som har de angivna namnen.
Jokertecken stöds.

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

### -Återkommer

Anger att den här cmdleten endast får resultat från det angivna jobbet.
Som standard `Receive-Job` hämtar också resultaten för alla underordnade jobb för det angivna jobbet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger en matris med sessioner.
Den här cmdleten hämtar resultatet av jobb som kördes i den angivna PowerShell-sessionen (**PSSession**).
Ange en variabel som innehåller **PSSession** eller ett kommando som hämtar **PSSession**, till exempel ett `Get-PSSession` kommando.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Vänta

Anger att denna cmdlet undertrycker kommando tolken tills alla jobb resultat tas emot.
Som standard `Receive-Job` returnerar omedelbart de tillgängliga resultaten.

Som standard väntar parametern **wait** tills jobbet är i något av följande tillstånd:

- Slutförd
- Misslyckad
- Stoppad
- Inaktiverad
- Frånkopplad.

Om du vill att **wait** -parametern ska fortsätta vänta om jobb tillståndet är inaktiverat eller frånkopplat använder du parametern **Force** tillsammans med parametern **wait** .

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

### -WriteEvents

Anger att denna cmdlet rapporterar ändringar i jobb tillstånd medan den väntar på att jobbet ska slutföras.

Den här parametern är endast giltig när parametern **wait** används i kommandot och parametern **Keep** utelämnas.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WriteJobInResults

Anger att den här cmdleten returnerar jobbobjektet följt av resultaten.

Den här parametern är endast giltig när parametern **wait** används i kommandot och parametern **Keep** utelämnas.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).

## INDATA

### System. Management. Automation. job

Du kan skicka pipe-jobb objekt till denna cmdlet.

## UTDATA

### PSObject

Den här cmdleten returnerar resultatet av kommandona i jobbet.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Invoke-kommando](Invoke-Command.md)

[Ta bort – jobb](Remove-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Wait-Job](Wait-Job.md)

