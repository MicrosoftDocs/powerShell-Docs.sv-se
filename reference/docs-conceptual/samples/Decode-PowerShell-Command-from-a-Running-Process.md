---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Avkoda ett PowerShell-kommando från en process som körs
author: randomnote1
description: Den här artikeln visar hur du avkodar ett skript block som en PowerShell-process körs för tillfället.
ms.openlocfilehash: 95b4b806665bf8137712ebb183329039bc1e1deb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500495"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Avkoda ett PowerShell-kommando från en process som körs

Ibland kan du ha en PowerShell-process som körs med en stor mängd resurser.
Den här processen kan köras i kontexten för ett jobb i [Schemaläggaren][] eller ett [SQL Server Agent][] jobb. Om det finns flera PowerShell-processer som körs kan det vara svårt att veta vilken process som representerar problemet. Den här artikeln visar hur du avkodar ett skript block som en PowerShell-process körs för tillfället.

## <a name="create-a-long-running-process"></a>Skapa en tids krävande process

Öppna ett nytt PowerShell-fönster och kör följande kod för att demonstrera det här scenariot. Den kör ett PowerShell-kommando som matar ut ett tal varje minut i 10 minuter.

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

Bröd texten i kommandot som PowerShell körs i lagras i egenskapen **CommandLine** i klassen [Win32_Process][] . Om kommandot är ett kodat kommando innehåller **CommandLine** -egenskapen strängen "EncodedCommand". Med hjälp av den här informationen kan det kodade kommandot vara avfördunkladede genom följande process.

Starta PowerShell som administratör. Det är viktigt att PowerShell körs som administratör, annars returneras inga resultat när du kör frågor mot de processer som körs.

Kör följande kommando för att hämta alla PowerShell-processer som har ett kodat kommando:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Följande kommando skapar ett anpassat PowerShell-objekt som innehåller process-ID och det kodade kommandot.

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

Nu kan det kodade kommandot avkodas. Följande fragment upprepas över kommando informations objekt, avkodar det kodade kommandot och lägger till det avkodade kommandot tillbaka till objektet för ytterligare undersökning.

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

Det avkodade kommandot kan nu granskas genom att välja den avkodade kommando egenskapen.

```Output
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
