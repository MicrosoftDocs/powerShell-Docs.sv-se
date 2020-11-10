---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388543"
---
# Resume-Job

## SAMMANFATTNING
Startar om ett pausat jobb.

## SYNTAX

### SessionIdParameterSet (standard)

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Resume-Job`Cmdleten återupptar ett arbets flödes jobb som har pausats, till exempel med hjälp av `Suspend-Job` cmdleten eller aktiviteten [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) . När ett arbets flödes jobb återupptas konstruerar jobb motorn om status, metadata och utdata från sparade resurser, t. ex. kontroll punkter. Jobbet startas om utan att tillstånd eller data går förlorade.
Jobb tillståndet har ändrats från **pausad** till att **köras**.

Använd parametrarna för `Resume-Job` för att välja jobb efter namn, ID, instans-ID eller pipe ett jobb objekt, till exempel ett som returneras av `Get-Job` cmdleten, till `Resume-Job` . Du kan också använda ett egenskaps filter för att välja ett jobb som ska återupptas.

Som standard `Resume-Job` returneras omedelbart, även om alla jobb kanske inte återupptas ännu. Om du vill ignorera kommando tolken tills alla angivna jobb har återupptagits, använder du parametern **wait** .

`Resume-Job`Cmdleten fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb. Den fungerar inte på vanliga bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten. Om du skickar ett jobb av en typ som inte stöds `Resume-Job` genererar ett avslutande fel och slutar att köras.

Du identifierar ett arbets flödes jobb genom att leta efter värdet **PSWorkflowJob** i **PSJobTypeName** -egenskapen för jobbet. Information om hur du avgör om en viss anpassad Jobbtyp stöder `Resume-Job` cmdleten finns i hjälp avsnitten för den anpassade jobb typen.

Innan du använder en jobb-cmdlet på en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen, antingen med hjälp av `Import-Module` cmdleten eller hämtar eller använder en cmdlet i modulen.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: återuppta ett jobb efter ID

Kommandona i det här exemplet kontrollerar att jobbet är ett pausat arbets flödes jobb och sedan återupptar jobbet. Det första kommandot använder `Get-Job` cmdleten för att hämta jobbet. Utdata visar att jobbet är ett pausat arbets flödes jobb. Det andra kommandot använder cmdlet **:** en för cmdlet: en för `Resume-Job` att återuppta jobbet med **ID-** värdet 4.

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### Exempel 2: återuppta ett jobb efter namn

Det här kommandot använder parametern **Name** för att återuppta flera arbets flödes jobb på den lokala datorn.

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### Exempel 3: Använd anpassade egenskaps värden

Det här kommandot använder värdet för en anpassad egenskap för att identifiera det arbets flödes jobb som ska återupptas. Den använder **filter** parametern för att identifiera arbets flödes jobbet med egenskapen **CustomID** . Den använder också parametern **State** för att kontrol lera att arbets flödes jobbet har pausats innan det försöker återuppta det.

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### Exempel 4: återuppta alla pausade jobb på en fjärrdator

Det här kommandot återupptar alla pausade jobb på den fjärranslutna SRV01-datorn.

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

Kommandot använder `Invoke-Command` cmdleten för att köra ett kommando på datorn SRV01. Fjärrkommandot använder cmdleten **State** för `Get-Job` cmdleten för att hämta alla pausade jobb på datorn. En pipeline-operator ( `|` ) skickar de pausade jobben till `Resume-Job` cmdleten, som återupptar dem.

### Exempel 5: vänta tills jobben återupptas

Det här kommandot använder parametern **wait** för att `Resume-Job` endast returnera när alla angivna jobb har återupptagits. Parametern **wait** är särskilt användbar i skript som förutsätter att jobb återupptas innan skriptet fortsätter.

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### Exempel 6: återuppta ett arbets flöde som pausar sig själv

I det här kod exemplet visas `Suspend-Workflow` aktiviteten i ett arbets flöde.

`Test-Suspend`Arbets flödet på Server01-datorn. När du kör arbets flödet kör arbets flödet `Get-Date` aktiviteten och lagrar resultatet i `$a` variabeln. Sedan körs `Suspend-Workflow` aktiviteten. Som svar tar det en kontroll punkt, pausar arbets flödet och returnerar ett arbets flödes jobb objekt. `Suspend-Workflow` Returnerar ett arbets flödes jobb objekt även om arbets flödet inte körs explicit som ett jobb.

`Resume-Job` återupptar `Test-Suspend` arbets flödet i Job8. Parametern **wait** används för att lagra kommando tolken tills jobbet återupptas.

`Receive-Job`Cmdlet: en hämtar resultatet av `Test-Suspend` arbets flödet. Det sista kommandot i arbets flödet returnerar ett **TimeSpan** -objekt som representerar den förflutna tiden mellan aktuellt datum och tid och datum och tid som sparades i `$a` variabeln innan arbets flödet pausades.

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

Med `Resume-Job` cmdleten kan du återuppta ett arbets flödes jobb som har pausats med hjälp av `Suspend-Workflow` aktiviteten. Den här aktiviteten pausar ett arbets flöde i ett arbets flöde. Den är endast giltig i arbets flöden.

Information om finns `Suspend-Workflow` i about_Suspend-Workflow] (.. /PSWorkflow/about/about_Suspend-Workflow. MD).

## PARAMETRAR

### -Filter

Anger en hash-tabell med villkor. Den här cmdleten återupptar jobb som uppfyller alla villkor i hash-tabellen. Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

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

### -ID

Anger en matris med ID: n för jobb som denna cmdlet återupptar.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen. Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen. Du kan ange ett eller flera ID: n, avgränsade med kommatecken. Kör för att hitta ID: t för ett jobb `Get-Job` .

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

Anger en matris med instans-ID: n för jobb som denna cmdlet återupptar. Standardvärdet är alla jobb.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn. Kör om du vill hitta instans-ID: t för ett jobb `Get-Job` .

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

Anger vilka jobb som ska återupptas. Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben. Du kan också skicka vidare jobb till- `Resume-Job` cmdleten.

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

Anger en matris med användarvänliga namn på jobb som denna cmdlet återupptar. Ange ett eller flera jobb namn.
Jokertecken är tillåtna.

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

Anger tillstånd för jobb som ska återupptas. De acceptabla värdena för den här parametern är:

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

Denna cmdlet återupptar bara jobb i tillståndet **Suspended** .

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

### – Vänta

Anger att denna cmdlet undertrycker kommando tolken tills alla jobb resultat har startats om. Som standard returnerar denna cmdlet omedelbart de tillgängliga resultaten.

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

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

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

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

Du kan skicka vidare alla typer av jobb till denna cmdlet. Om `Resume-Job` hämtar ett jobb av en typ som inte stöds returneras ett avslutande fel.

## UTDATA

### Ingen, system. Management. Automation. job

Den här cmdleten returnerar de jobb som det försöker återuppta, om du använder parametern **Passthru** .
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- `Resume-Job` Det går bara att återuppta jobb som har pausats. Om du skickar ett jobb med ett annat tillstånd `Resume-Job` Kör återställnings åtgärden för jobbet, men genererar en varning för att meddela att det inte gick att återuppta jobbet. Om du vill utelämna varningen använder du den gemensamma parametern **WarningAction** med värdet SilentlyContinue.
- Om ett jobb inte är av en typ som har stöd för att återuppta, till exempel ett arbets flödes jobb ( **PSWorkflowJob** ), `Resume-Job` returnerar ett avslutande fel.
- Mekanismen och platsen för att spara ett pausat jobb kan variera beroende på jobb typen. Till exempel sparas pausade arbets flödes jobb i ett Flat File-Arkiv som standard, men kan också sparas i en SQL-databas.
- När du återupptar ett jobb ändras jobb tillståndet från **pausat** till att **köras**. Om du vill hitta jobb som kör, inklusive de som har återupptagits av denna cmdlet, använder du parametern **State** för cmdlet: en `Get-Job` för att hämta jobb i **körnings** tillstånd.
- Vissa jobb typer har alternativ eller egenskaper som förhindrar att Windows PowerShell pausar jobbet.
  Om försök att pausa jobbet Miss lyckas, kontrollerar du att alternativen och egenskaperna för jobbet kan avbrytas.

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Pausa – jobb](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
