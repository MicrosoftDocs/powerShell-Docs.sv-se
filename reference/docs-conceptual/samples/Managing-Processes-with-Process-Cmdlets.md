---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Hantera processer med Process-cmdletar
description: PowerShell innehåller flera cmdletar som hjälper dig att hantera processer på lokala datorer och fjärrdatorer.
ms.openlocfilehash: 977a3459eeac22536341753ccd59357d718745f2
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500444"
---
# <a name="managing-processes-with-process-cmdlets"></a>Hantera processer med Process-cmdletar

Du kan använda process-cmdletar i Windows PowerShell för att hantera lokala och fjärranslutna processer i Windows PowerShell.

## <a name="getting-processes-get-process"></a>Hämtar processer (Get-process)

Kör en **Get-process** utan parametrar för att hämta processerna som körs på den lokala datorn.

Du kan hämta specifika processer genom att ange deras process namn eller process-ID. Följande kommando hämtar inaktiva processen:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Även om det är normalt för cmdlets att returnera inga data i vissa situationer, genererar **Get-process** ett fel om den inte hittar några matchningar, eftersom den vanliga avsikten är att hämta en känd process som körs. Om det inte finns någon process med detta ID är det troligt att ID: t är felaktigt eller att ränte processen redan har avslut ATS:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Du kan använda parametern name i Get-Process-cmdlet: en för att ange en delmängd av processerna baserat på processens namn. Parametern name kan ta flera namn i en kommaavgränsad lista och den stöder användning av jokertecken, så du kan skriva namn mönster.

Följande kommando hämtar till exempel de namn som börjar med "ex".

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Eftersom .NET system. Diagnostics. process-klassen är grunden för Windows PowerShell-processer, följer några av de konventioner som används av system. Diagnostics. process. En av dessa konventioner är att process namnet för en körbar fil aldrig innehåller ". exe" i slutet av namnet på den körbara filen.

**Get-process** accepterar också flera värden för parametern name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Du kan använda parametern ComputerName för Get-Process för att få processer på fjärrdatorer. Följande kommando hämtar till exempel PowerShell-processerna på den lokala datorn (representeras av "localhost") och på två fjärrdatorer.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Dator namnen är inte tydliga i den här vyn, men de lagras i egenskapen MachineName för de process objekt som Get-Process returnerar. Följande kommando använder Format-Table-cmdleten för att visa egenskaperna process-ID, ProcessName och MachineName (ComputerName) för process objekt.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 |
  Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Detta mer komplexa kommando lägger till egenskapen MachineName till standard Get-Processs visning.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Stoppa processer (Stop-process)

Med Windows PowerShell får du flexibilitet för att visa processer, men vad händer om du stoppar en process?

Cmdleten **Stop process** tar ett namn eller ID för att ange en process som du vill stoppa. Din möjlighet att stoppa processer beror på dina behörigheter. Det går inte att stoppa vissa processer. Om du till exempel försöker stoppa inaktiva processer får du ett fel meddelande:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Du kan också tvinga fram en fråga med **Confirm** -parametern. Den här parametern är särskilt användbar om du använder ett jokertecken när du anger process namnet, eftersom det kan hända att du råkar matcha vissa processer som du inte vill stoppa:

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

Det går att hantera komplexa processer med några av objekt filtrerings-cmdletarna. Eftersom ett process objekt har en svarande-egenskap som är sann när den inte längre svarar kan du stoppa alla program som inte svarar med följande kommando:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Du kan använda samma metod i andra situationer. Anta till exempel att ett sekundärt meddelande fält program körs automatiskt när användare startar ett annat program. Det kanske inte fungerar korrekt i Terminal Services-sessioner, men du vill fortfarande behålla det i sessioner som körs på den fysiska dator konsolen. Sessioner som är anslutna till den fysiska datorns dator har alltid sessions-ID 0, så du kan stoppa alla instanser av processen som finns i andra sessioner genom att använda **Where-Object** och processen, **SessionID**:

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Stop-Process-cmdleten har ingen ComputerName-parameter. Om du vill köra kommandot Stop process på en fjärrdator måste du därför använda Invoke-Command-cmdleten. Om du till exempel vill stoppa PowerShell-processen på fjärrdatorn Server01 skriver du:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Stoppa alla andra Windows PowerShell-sessioner

Det kan ibland vara användbart att kunna stoppa alla andra Windows PowerShell-sessioner som körs, förutom den aktuella sessionen. Om en session använder för många resurser eller inte går att komma åt (den kan köras via fjärr anslutning eller i en annan fjärrskrivbordssession), kanske du inte kan stoppa den direkt. Om du försöker stoppa alla pågående sessioner kan den aktuella sessionen avslutas i stället.

Varje Windows PowerShell-session har en miljö variabel i PID som innehåller ID: t för Windows PowerShell-processen. Du kan kontrol lera $PID mot ID: t för varje session och endast Avsluta Windows PowerShell-sessioner som har ett annat ID. Följande pipeline-kommando gör detta och returnerar listan över avslutade sessioner (på grund av användningen av parametern **Passthru** ):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>Starta, felsöka och vänta på processer

Windows PowerShell levereras också med cmdlets för att starta (eller starta om), felsöka en process och vänta tills processen har slutförts innan du kör ett kommando. Information om dessa cmdlets finns i hjälp avsnittet om cmdleten för varje cmdlet.

## <a name="see-also"></a>Se även

- [Hämta process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)
- [Stoppa – process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)
- [Start process](/powershell/module/Microsoft.PowerShell.Management/Start-Process)
- [Vänta-process](/powershell/module/Microsoft.PowerShell.Management/Wait-Process)
- [Fel sökning – process](/powershell/module/Microsoft.PowerShell.Management/Debug-Process)
- [Invoke-kommando](/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)
