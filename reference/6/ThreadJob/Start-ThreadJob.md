---
external help file: ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 01/28/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: debe4002ec4d7ba7651f739316c4127243d8ebd3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266919"
---
# Start-ThreadJob

## SAMMANFATTNING
Skapar bakgrunds jobb som liknar- `Start-Job` cmdleten.

## SYNTAX

### Script block

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### FilePath

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Start-ThreadJob` skapar bakgrunds jobb som liknar- `Start-Job` cmdleten. Den största skillnaden är att jobben som skapas körs i separata trådar i den lokala processen. Som standard använder jobben den aktuella arbets katalogen för den anropare som startade jobbet.

Cmdleten stöder också en **ThrottleLimit** -parameter för att begränsa antalet jobb som körs samtidigt. När fler jobb startas placeras de i kö och väntar tills det aktuella antalet jobb sjunker under begränsnings gränsen.

## EXEMPEL

### Exempel 1 – Skapa bakgrunds jobb med en tråd gräns på 2

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### Exempel 2 – Jämför prestanda för Start-Job och Start-ThreadJob

I det här exemplet visas skillnaden mellan `Start-Job` och `Start-ThreadJob` . Jobben kör `Start-Sleep` cmdleten för 1 sekund. Eftersom jobben körs parallellt, är den totala körnings tiden ungefär 1 sekund, och varje gång som krävs för att skapa jobben.

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

När du har subtraherat 1 sekund för körnings tid kan du se att det `Start-Job` tar cirka 4,8 sekunder att skapa fem jobb. `Start-ThreadJob` är 8 gånger snabbare, tar cirka 0,6 sekunder att skapa fem jobb. Resultaten kan variera i din miljö, men den relativa förbättringen bör vara densamma.

### Exempel 3 – skapa jobb med InputObject

I det här exemplet använder skript block `$input` variabeln för att ta emot ininformation från **InputObject** -parametern. Detta kan också göras av rör objekt till `Start-ThreadJob` .

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

## PARAMETRAR

### – Argument List

Anger en matris med argument eller parameter värden för det skript som anges av **fil Sök vägen** eller **script block** -parametrarna.

**Argument List** måste vara den sista parametern på kommando raden. Alla värden som följer efter parameter namnet tolkas som värden i argument listan.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger en skript fil som ska köras som ett bakgrunds jobb. Ange sökvägen och fil namnet för skriptet. Skriptet måste finnas på den lokala datorn eller i en mapp som den lokala datorn kan komma åt.

När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block och kör skript blocket som ett bakgrunds jobb.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Anger kommandon som körs innan jobbet startas. Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.

Använd den här parametern för att förbereda sessionen där jobbet körs. Du kan till exempel använda den för att lägga till funktioner och moduler i sessionen.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska användas som inmatade för skript blocket. Du kan också använda pipeline-ingångar. Använd den `$input` automatiska variabeln i-skript blocket för att komma åt objekten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger ett eget namn för det nya jobbet. Du kan använda namnet för att identifiera jobbet till andra jobb-cmdlet: ar, till exempel `Stop-Job` cmdleten.

Det egna standardnamnet är "Job #", där "#" är ett ordnings tal som ökar för varje jobb.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block

Anger vilka kommandon som ska köras i bakgrunds jobbet. Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block. Använd den `$Input` automatiska variabeln för att få åtkomst till värdet för parametern **InputObject** . Den här parametern är obligatorisk.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Den här parametern begränsar antalet jobb som körs samtidigt. När jobben startas placeras de i kö och väntar tills en tråd är tillgänglig i trådpoolen för att köra jobbet. Standard gränsen är 5 trådar.

Storleken på trådpoolen är global till PowerShell-sessionen. Om du anger en **ThrottleLimit** i ett anrop anges gränsen för efterföljande anrop i samma session.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

## UTDATA

### ThreadJob.ThreadJob

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Start – jobb](../Microsoft.PowerShell.Core/Start-Job.md)

[Stoppa – jobb](../Microsoft.PowerShell.Core/Stop-Job.md)

[Mottagning – jobb](../Microsoft.PowerShell.Core/Receive-Job.md)
