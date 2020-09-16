---
title: Visa förloppet under multi-threading
description: Så här använder du Skriv förloppet över flera trådar med en förgrunds-objekt-parallell
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410850"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a>Skriv förlopp över flera trådar med förgrunds parallell

Från och med PowerShell 7,0 är möjligheten att arbeta i flera trådar samtidigt möjlig med hjälp av **Parallel** -parametern i [-objekt-](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdleten. Det kan vara en utmaning att övervaka förloppet för dessa trådar. Normalt kan du övervaka förloppet för en process med hjälp av [Skriv förloppet](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).
Men eftersom PowerShell använder sig av en separat körnings utrymme för varje tråd när de använder **parallellt**, så rapporterar inte återställningen till värden lika enkelt som normal användning av `Write-Progress` .

## <a name="using-a-synced-hashtable-to-track-progress"></a>Använda en synkroniserad hash för att spåra förloppet

När du skriver förloppet från flera trådar blir spårningen svår eftersom när parallella processer körs i PowerShell, och varje process har det egna körnings utrymme. Du kan komma runt detta genom att använda en [synkroniserad hash](/dotnet/api/system.collections.hashtable.synchronized). En synkroniserad hash-post är en tråd säker data struktur som kan ändras av flera trådar samtidigt utan att ett fel utlöses.

### <a name="set-up"></a>Konfigurera

En av nackerna med den här metoden är att det tar en, ganska komplicerad inställning att se till att allt körs utan fel.

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

I det här avsnittet skapas tre olika data strukturer i tre olika syfte.

`$dataSet`Variabeln lagrar en matris med hash som används för att koordinera nästa steg utan att risken ändras. Om en objekt samling ändras när du går igenom samlingen, genererar PowerShell ett fel. Du måste behålla objekt samlingen i slingan separat från de objekt som ändras. `Id`Nyckeln i varje hash-tabellen är identifieraren för en modell process. `Wait`Nyckeln simulerar arbets belastningen för varje modell process som spåras.

`$origin`Variabeln lagrar en kapslad hash-tabell med varje nyckel som en av de blå process-ID: t.
Sedan används den för att torka den synkroniserade hash-filen som lagras i `$sync` variabeln. `$sync`Variabeln ansvarar för rapportering av förloppet till den överordnade körnings utrymme, som visar förloppet.

### <a name="running-the-processes"></a>Köra processerna

I det här avsnittet körs multi-threaded-processer och skapar några av de utdata som används för att visa förloppet.

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

De blå processerna skickas till `Foreach-Object` och startas som jobb. **ThrottleLimit** har angetts till **3** för att markera att köra flera processer i en kö. Jobben lagras i `$job` variabeln och gör det möjligt för oss att veta när alla processer har avslut ATS senare.

När du använder `using:` instruktionen för att referera till en överordnad omfångs variabel i PowerShell kan du inte använda uttryck för att göra den dynamisk. Om du till exempel försökte skapa `$process` variabeln som detta, `$process = $using:sync.$($PSItem.id)` får du ett fel meddelande om att du inte kan använda uttryck där. Därför skapar vi `$syncCopy` variabeln för att kunna referera till och ändra `$sync` variabeln utan att risken för den fungerar.

Därefter skapar vi en hash-hash som representerar förloppet för processen i slingan med `$process` variabeln genom att referera till synkroniserade hash-nycklar. **Aktivitet** och **status** nycklar används som parameter värden för `Write-Progress` för att visa statusen för en specifik skiss process i nästa avsnitt.

`foreach`Slingan är bara ett sätt att simulera processen och är slumpmässig baserat på `$dataSet` attributet **wait** för att ställa in `Start-Sleep` i millisekunder. Hur du beräknar processens förlopp kan variera.

### <a name="displaying-the-progress-of-multiple-processes"></a>Visa förloppet för flera processer

Nu när de blå processerna körs som jobb kan vi börja skriva process förloppet till PowerShell-fönstret.

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

`$job`Variabeln innehåller det överordnade **jobbet** och har ett underordnat **jobb** för var och en av de blå processerna. När något av de underordnade jobben fortfarande körs förblir det överordnade jobbets **tillstånd** "körs". Detta gör att vi kan använda `while` loopen för att kontinuerligt uppdatera förloppet för varje process tills alla processer har slutförts.

I loopen loopar vi igenom var och en av nycklarna i `$sync` variabeln. Eftersom det här är en synkroniserad hash-uppdatering, uppdateras den ständigt men kan fortfarande användas utan att några fel utlöses.

Det finns en kontroll för att se till att den process som rapporteras verkligen körs med hjälp av `IsNullOrEmpty()` metoden. Om processen inte har startats rapporterar inte loopen och går vidare till nästa tills den får en process som har startats. Om processen startas används hash-tabellen från den aktuella nyckeln för att splat parametrarna till `Write-Progress` .

### <a name="full-example"></a>Fullständigt exempel

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a>Relaterade länkar

- [about_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [about_Scopes](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [about_Splatting](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
