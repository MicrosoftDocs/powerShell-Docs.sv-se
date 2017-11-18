---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Hantera processer med Process-Cmdlets
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 3786fb77167746d6a477dffdd4ea13e863c99964
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="managing-processes-with-process-cmdlets"></a>Hantera processer med Process-Cmdlets
Du kan använda Process-cmdlets i Windows PowerShell för att hantera lokala processer och fjärrprocesser i Windows PowerShell.

## <a name="getting-processes-get-process"></a>Hämtar processer (Get-Process)
För att få de processer som körs på den lokala datorn kan köra en **Get-Process** utan parametrar.

Vissa processer får du genom att ange sina processnamn eller process-ID. Följande kommando hämtar den inaktiva processen:

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Även om det är normalt för cmdletar för att returnera några data i vissa situationer när du anger en process med dess ProcessId **Get-Process** genererar ett fel om den hittar inga matchningar eftersom vanliga avsikten är att hämta en känd process som körs. Om det inte finns någon process med detta Id, är det troligt att Id är felaktigt eller att processen intressanta har redan avslutats:

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Du kan använda Name-parametern i cmdleten Get-Process för att ange en delmängd av processer baserat på processens namn. Parametern Name kan ta flera namn i en kommaavgränsad lista och den stöder användning av jokertecken, så att du kan skriva namnet mönster.

Till exempel hämtar följande kommando processen vars namn börjar med ”t.ex”.

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Eftersom .NET System.Diagnostics.Process klass är grunden för Windows PowerShell-processer, följer några av de konventioner som används av System.Diagnostics.Process. En av dessa konventioner är att processnamn för en körbar fil aldrig innehåller ”.exe” i slutet av namnet på programfilen.

**Get-Process** också accepterar flera värden för parametern namn.

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Du kan använda parametern ComputerName av Get-Process för att hämta processer på fjärrdatorer. Till exempel följande kommando hämtar PowerShell processer på den lokala datorn (som representeras av ”localhost”) och på två fjärranslutna datorer.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Datornamn som är inte uppenbara som visas, men de lagras i egenskapen MachineName process-objekt som returneras av Get-Process. Följande kommando använder Format-Table-cmdlet för att visa process-ID, processnamn och MachineName (datornamn) egenskaper för process-objekt.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Mer komplexa kommandot lägger till egenskapen MachineName standard Get-Process visningen. Backtick (\`)(ASCII 96) är Windows PowerShell fortsättning tecken.

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Stoppa processer (Stop-Process)
Windows PowerShell ger flexibilitet för att visa processer, men vad händer om stoppa en process?

Den **stoppa processen** cmdlet tar ett namn eller Id för att ange en process som du vill stoppa. Du kan stoppa processer beror på dina behörigheter. Vissa processer kan inte stoppas. Du får till exempel ett fel vid försök att stoppa den inaktiva processen:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Du kan också tvinga fråga med den **Bekräfta** parameter. Den här parametern är särskilt användbar om du använder jokertecken när du anger processnamn, eftersom du av misstag kan matcha vissa processer som du inte vill stoppa:

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

Komplex process manipulation är möjligt med objektet filtrering cmdlets. Eftersom en Process-objektet har en svarar-egenskap som är sant när svarar inte längre kan stoppa du alla program som inte svarar med följande kommando:

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Du kan använda samma metod i andra situationer. Anta exempelvis att en sekundär notification område programmet körs automatiskt när användarna startar ett annat program. Du kanske att det inte fungerar korrekt i Terminal Services-sessioner, men du ändå vill hålla i sessioner som körs på den fysiska dator-konsolen. Sessioner som är anslutna till fysiska datorns skrivbord alltid har ett sessions-ID 0, så du kan stoppa alla instanser av processen, som i andra sessioner med hjälp av **Where-Object** och processen **SessionId** :

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Cmdlet Stop-Process har inte en parametern ComputerName. För att köra kommandot stoppa processen på en fjärrdator, måste du därför använda cmdleten Invoke-Command. Om du vill stoppa processen PowerShell på fjärrdatorn Server01, exempelvis:

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Stoppa alla andra Windows PowerShell-sessioner
Det kan ibland vara användbara för att kunna stoppa alla körs Windows PowerShell-sessioner än den aktuella sessionen. Om en session använder för många resurser eller inte är tillgänglig (det kan köras via fjärranslutning eller i en annan skrivbordssession), du kan inte stoppa den direkt. Om du försöker att stoppa alla pågående sessioner, men avslutas den aktuella sessionen i stället.

Varje Windows PowerShell-sessionen har en miljövariabel PID som innehåller Id för Windows PowerShell-process. Du kan kontrollera $PID mot Id för varje session och avsluta endast Windows PowerShell-sessioner som har ett annat Id. Kommandot pipeline gör detta och returnerar listan över avslutade sessioner (på grund av användningen av den **PassThru** parametern):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>Starta felsökning och väntar på processer
Windows PowerShell innehåller också cmdletar för att starta (eller starta om) debug en process och vänta tills en process för att slutföra innan du kör ett kommando. Information om dessa cmdlets finns i cmdlet-hjälpavsnittet för varje cmdlet.

## <a name="see-also"></a>Se även
- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Vänta-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
