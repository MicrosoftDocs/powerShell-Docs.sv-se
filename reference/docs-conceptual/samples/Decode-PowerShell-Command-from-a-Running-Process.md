---
ms.date: 11/13/2018
keywords: PowerShell cmdlet
title: Avkoda ett PowerShell-kommando från en process som körs
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086246"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Avkoda ett PowerShell-kommando från en process som körs

Du kan ibland ha ett PowerShell process som körs som tar upp mycket resurser.
Den här processen kan köras i samband med en [Schemaläggaren][] jobb eller en [SQL Server Agent][] jobbet. Där det finns flera PowerShell-processer som körs, kan det vara svårt att veta vilken process representerar problemet. Den här artikeln visar hur du avkoda ett skriptblock som en PowerShell-process körs för tillfället.

## <a name="create-a-long-running-process"></a>Skapa en tidskrävande process

Öppna ett nytt PowerShell-fönster och kör följande kod för att visa det här scenariot. Den körs en PowerShell-kommando som matar ut ett tal i minuten i 10 minuter.

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a>Visa processen

Brödtexten i det kommando som kör PowerShell lagras i den **CommandLine** egenskapen för den [Win32_Process][] klass. Om kommandot är en [kodad kommandot][], **CommandLine** egenskap innehåller strängen ”EncodedCommand”. Med den här informationen kan kan kommandot kodade inte ta bort dold via följande process.

Starta PowerShell som administratör. Det är viktigt att PowerShell kör som administratör, annars returneras inga resultat vid frågor till processer som körs.

Kör följande kommando för att hämta alla PowerShell-processer som har en kodad kommando:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Följande kommando skapar en anpassad PowerShell-objekt som innehåller process-ID och kommandot kodad.

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

Nu kan kommandot kodade avkodas. Följande kodavsnitt itererar över information kommandoobjektet avkodar kommandot kodade och lägger till det avkodade kommandot tillbaka till objektet för vidare studier.

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

Kommandot avkodade kan nu granskas genom att välja avkodade Kommandoegenskapen.

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Schemaläggaren]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[kodad kommandot]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
