---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52613dae3ba73227818c6c0dec40183ba20ce2a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710452"
---
# Remove-Job

## SAMMANFATTNING
Tar bort ett PowerShell-bakgrunds jobb.

## SYNTAX

### SessionIdParameterSet (standard)

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandParameterSet

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Remove-Job`Cmdlet: en tar bort PowerShell-bakgrunds jobb som startades av `Start-Job` cmdleten eller av cmdlets som `Invoke-Command` stöder parametern **AsJob** .

Du kan använda `Remove-Job` för att ta bort alla jobb eller ta bort valda jobb. Jobben identifieras med **namn**, **ID**, **instans-ID**, **kommando** eller **tillstånd**. Eller så kan ett jobb objekt skickas nedåt i pipeline till `Remove-Job` . Utan parametrar eller parameter värden `Remove-Job` har ingen påverkan.

Eftersom PowerShell 3,0 `Remove-Job` kan ta bort anpassade jobb typer, till exempel schemalagda jobb och arbets flödes jobb. Till exempel `Remove-Job` tar bort det schemalagda jobbet, alla instanser av det schemalagda jobbet på disken och resultatet av alla Utlös ande jobb instanser.

Om du försöker ta bort ett jobb som körs `Remove-Job` Miss lyckas. Använd `Stop-Job` cmdleten för att stoppa ett pågående jobb. Eller Använd `Remove-Job` med parametern **Force** för att ta bort ett jobb som körs.

Jobb finns kvar i den globala jobb-cachen tills du tar bort bakgrunds jobbet eller stänger PowerShell-sessionen.

## EXEMPEL

### Exempel 1: ta bort ett jobb med hjälp av dess namn

I det här exemplet används en variabel och pipelinen för att ta bort ett jobb efter namn.

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

`Get-Job` använder parametern **Name** för att ange jobbet **BatchJob**. Jobbobjektet lagras i `$batch` variabeln. Objektet i `$batch` skickas pipelinen till `Remove-Job` .

Ett alternativ är att använda **jobb** parametern, till exempel `Remove-Job -Job $batch` .

### Exempel 2: ta bort alla jobb i en session

I det här exemplet tas alla jobb i den aktuella PowerShell-sessionen bort.

```powershell
Get-job | Remove-Job
```

`Get-Job` hämtar alla jobb i den aktuella PowerShell-sessionen. Jobb objekten skickas ned pipelinen till `Remove-Job` .

### Exempel 3: ta bort NotStarted-jobb

Det här exemplet tar bort alla jobb från den aktuella PowerShell-sessionen som inte har startats.

```powershell
Remove-Job -State NotStarted
```

`Remove-Job` använder parametern **State** för att ange jobbets status.

### Exempel 4: ta bort jobb med ett eget namn

Det här exemplet tar bort alla jobb från den aktuella sessionen med egna namn som slutar med * batch * *, inklusive jobb som kör.

```powershell
Remove-Job -Name *batch -Force
```

`Remove-Job` använder parametern **Name** för att ange ett jobb namns mönster. Mönstret innehåller jokertecknet asterisk ( `*` ) för att hitta alla jobb namn som slutar med **batch**. Parametern **Force** tar bort jobb som kör.

### Exempel 5: ta bort ett jobb som har skapats av Invoke-Command

Det här exemplet tar bort ett jobb som startades på en fjärrdator med hjälp `Invoke-Command` av parametern **AsJob** .

Eftersom exemplet använder parametern **AsJob** skapas jobbobjektet på den lokala datorn.
Men jobbet körs på en fjärrdator. Därför använder du lokala kommandon för att hantera jobbet.

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

`Invoke-Command` kör ett jobb på den **Server01** datorn. Parametern **AsJob** kör **script block** som ett bakgrunds jobb. Jobbobjektet lagras i `$job` variabeln. Det `$job` variabla objektet skickas nedåt i pipeline till `Remove-Job` .

### Exempel 6: ta bort ett jobb som har skapats av Invoke-Command och Start-Job

Det här exemplet visar hur du tar bort ett jobb på en fjärrdator som startades med hjälp av `Invoke-Command` att köra `Start-Job` . Jobbobjektet skapas på fjärrdatorn och fjärrkommandona används för att hantera jobbet. En permanent anslutning krävs när du kör ett `Start-Job` fjärrkommando.

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

`New-PSSession` skapar en **PSSession**, en permanent anslutning, till **Server01** -datorn. Anslutningen sparas i `$S` variabeln.

`Invoke-Command` ansluter till sessionen som sparats i `$S` . **Script block** använder `Start-Job` för att starta ett Fjärrjobb. Jobbet kör ett `Get-Process` kommando och använder parametern **Name** för att ange ett eget jobbnamn, **MyJob**.

`Invoke-Command` använder `$S` sessionen och körs `Remove-Job` . Parametern **Name** anger att jobbet med namnet **MyJob** har tagits bort.

### Exempel 7: ta bort ett jobb med hjälp av dess InstanceId

Det här exemplet tar bort ett jobb baserat på dess **InstanceID**.

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` startar ett bakgrunds jobb och jobbobjektet sparas i `$job` variabeln.

Objektet i `$job` skickas pipelinen till `Format-List` . **Egenskaps** parametern använder en asterisk ( `*` ) för att ange att alla objekt egenskaper ska visas i en lista.

`Remove-Job` använder parametern **InstanceID** för att ange det jobb som ska tas bort.

## PARAMETRAR

### -Kommando

Tar bort jobb som innehåller de angivna orden i kommandot. Du kan ange en kommaavgränsad matris.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan körs `Remove-Job` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Tar bort jobb som uppfyller alla villkor som fastställs i den tillhör ande hash-tabellen. Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb. Det fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` .

Den här parametern introduceras i PowerShell 3,0.

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

Tar bort ett jobb även om jobbets tillstånd **körs**. Om **Force** -parametern inte anges `Remove-Job` tar inte bort jobb som körs.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Tar bort bakgrunds jobb med angivet **ID**. Du kan ange en kommaavgränsad matris. Jobbets **ID** är ett unikt heltal som identifierar ett jobb inom den aktuella sessionen.

Använd utan parametrar för att hitta ett jobb **-ID** `Get-Job` .

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

Tar bort jobb med angivet **InstanceID**. Du kan ange en kommaavgränsad matris. Ett **InstanceID** är ett unikt GUID som identifierar ett jobb.

Använd om du vill hitta ett jobbs **InstanceID** `Get-Job` .

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

Anger vilka jobb som ska tas bort. Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben. Du kan ange en kommaavgränsad matris.

Du kan skicka jobb objekt nedåt i pipeline till `Remove-Job` .

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

Tar bara bort jobb med angivet eget namn. Jokertecken är tillåtna. Du kan ange en kommaavgränsad matris.

Användarvänliga namn för jobb garanterar inte att vara unika, även inom en PowerShell-session. Använd parametrarna **whatIf** och **Confirm** när du tar bort filer efter namn.

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

### – Tillstånd

Tar bara bort jobb med det angivna läget. Använd parametern **Force** om du vill ta bort jobb med statusen **körs**.

Godkända värden:

- AtBreakpoint
- Blockerad
- Slutförd
- Frånkopplad
- Misslyckad
- NotStarted
- Körs
- Stoppad
- Stoppas
- Inaktiverad
- Pausar

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Visar vad som händer om `Remove-Job` körs. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. job

Du kan skicka ett jobb objekt nedåt i pipeline till `Remove-Job` .

## UTDATA

### Inga

`Remove-Job` genererar inga utdata.

## ANTECKNINGAR

Ett PowerShell-jobb skapar en ny process. När jobbet har slutförts avslutas processen. När körs `Remove-Job` , tas jobbets tillstånd bort.

Om ett jobb avbryts innan det slutförs och processen inte har avslut ATS, tvingas processen att avslutas.

## RELATERADE LÄNKAR

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Hämta jobb](Get-Job.md)

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Wait-Job](Wait-Job.md)

