---
ms.date: 11/13/2018
keywords: PowerShell, cmdlet
title: Avkoda ett PowerShell-kommando från en process som körs
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "66470962"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="ba006-103">Avkoda ett PowerShell-kommando från en process som körs</span><span class="sxs-lookup"><span data-stu-id="ba006-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="ba006-104">Ibland kan du ha en PowerShell-process som körs med en stor mängd resurser.</span><span class="sxs-lookup"><span data-stu-id="ba006-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="ba006-105">Den här processen kan köras i kontexten för ett jobb i [Schemaläggaren][] eller ett [SQL Server Agent][] jobb.</span><span class="sxs-lookup"><span data-stu-id="ba006-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="ba006-106">Om det finns flera PowerShell-processer som körs kan det vara svårt att veta vilken process som representerar problemet.</span><span class="sxs-lookup"><span data-stu-id="ba006-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="ba006-107">Den här artikeln visar hur du avkodar ett skript block som en PowerShell-process körs för tillfället.</span><span class="sxs-lookup"><span data-stu-id="ba006-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="ba006-108">Skapa en tids krävande process</span><span class="sxs-lookup"><span data-stu-id="ba006-108">Create a long running process</span></span>

<span data-ttu-id="ba006-109">Öppna ett nytt PowerShell-fönster och kör följande kod för att demonstrera det här scenariot.</span><span class="sxs-lookup"><span data-stu-id="ba006-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="ba006-110">Den kör ett PowerShell-kommando som matar ut ett tal varje minut i 10 minuter.</span><span class="sxs-lookup"><span data-stu-id="ba006-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="ba006-111">Visa processen</span><span class="sxs-lookup"><span data-stu-id="ba006-111">View the process</span></span>

<span data-ttu-id="ba006-112">Bröd texten i kommandot som PowerShell körs i lagras i egenskapen **CommandLine** i klassen [Win32_Process][] .</span><span class="sxs-lookup"><span data-stu-id="ba006-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="ba006-113">Om kommandot är ett kodat kommando innehåller **CommandLine** -egenskapen strängen "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="ba006-113">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="ba006-114">Med hjälp av den här informationen kan det kodade kommandot vara avfördunkladede genom följande process.</span><span class="sxs-lookup"><span data-stu-id="ba006-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="ba006-115">Starta PowerShell som administratör.</span><span class="sxs-lookup"><span data-stu-id="ba006-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="ba006-116">Det är viktigt att PowerShell körs som administratör, annars returneras inga resultat när du kör frågor mot de processer som körs.</span><span class="sxs-lookup"><span data-stu-id="ba006-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="ba006-117">Kör följande kommando för att hämta alla PowerShell-processer som har ett kodat kommando:</span><span class="sxs-lookup"><span data-stu-id="ba006-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="ba006-118">Följande kommando skapar ett anpassat PowerShell-objekt som innehåller process-ID och det kodade kommandot.</span><span class="sxs-lookup"><span data-stu-id="ba006-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="ba006-119">Nu kan det kodade kommandot avkodas.</span><span class="sxs-lookup"><span data-stu-id="ba006-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="ba006-120">Följande fragment upprepas över kommando informations objekt, avkodar det kodade kommandot och lägger till det avkodade kommandot tillbaka till objektet för ytterligare undersökning.</span><span class="sxs-lookup"><span data-stu-id="ba006-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="ba006-121">Det avkodade kommandot kan nu granskas genom att välja den avkodade kommando egenskapen.</span><span class="sxs-lookup"><span data-stu-id="ba006-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

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
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
