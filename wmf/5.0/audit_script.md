---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684663"
---
# <a name="script-tracing-and-logging"></a>Skriptspårning och -loggning

Även om Windows PowerShell har redan den **LogPipelineExecutionDetails** Grupprincip att ställa in logga av cmdlet: ar, PowerShell-skriptspråket massor av funktioner som du kanske vill logga in och/eller granska. Den nya funktionen för detaljerad spårning av skriptet kan du aktivera detaljerad spårning och analys av Windows PowerShell skript används på ett system. När du har aktiverat detaljerad skriptet spårning av Windows PowerShell loggar alla skriptblocken händelseloggen ETW **Microsoft-Windows-PowerShell/Operational**. Om ett skriptblock skapar ett annat skriptblock (till exempel ett skript som anropar cmdleten Invoke-Expression på en sträng), loggas samt det resulterande skriptblocket.

Loggning av dessa händelser kan aktiveras via den **aktiverar loggning för PowerShell-skript Block** grupprincipinställningen (i Administrationsmallar -> Windows-komponenter -> Windows PowerShell).

Händelserna är:

| Kanal | Operativa                                 |
|---------|---------------------------------------------|
| Nivå   | Verbose                                     |
| OpCode  | Create                                      |
| Uppgift    | CommandStart                                |
| Nyckelord | körningsutrymme                                    |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Meddelande | Skapa Scriptblock text (%1% 2): </br> %3 </br> ScriptBlock ID: %4 |


Den text som bifogas i meddelandet är omfattningen av skriptblocket kompileras. ID: T är ett GUID som finns kvar för resten av skriptblocket.

När du aktiverar utförlig loggning kan funktionen skrivningar börja och sluta markörer:

| Kanal | Operativa                                            |
|---------|--------------------------------------------------------|
| Nivå   | Verbose                                                |
| OpCode  | Öppna (/ Stäng)                                         |
| Uppgift    | CommandStart (/ CommandStop)                           |
| Nyckelord | körningsutrymme                                               |
| EventId | ScriptBlock\_anropa\_starta\_detalj (0x1009 = 4105) / </br> ScriptBlock\_anropa\_fullständig\_detalj (0x100A = 4106) |
| Meddelande | Igång (/ slutförda) anrop av ScriptBlock-ID: %1 </br> Runspace ID: %2 |

ID: T är GUID som representerar skriptblocket (som kan korreleras med händelse-ID 0x1008) och Körningsutrymme-ID representerar runspace där skriptblocket kördes.

Procenttecken i anrop meddelandet representerar strukturerade ETW-egenskaper. När de ersätts med de faktiska värdena i meddelandetexten, ett mer robust sätt att komma åt dem är att hämta meddelandet med cmdleten Get-WinEvent och sedan använda den **egenskaper** matris med meddelandet.

Här är ett exempel på hur den här funktionen kan hjälpa dig att packa upp angripare att kryptera och Förvräng ett skript:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

Kör detta genererar följande loggposter:

```
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Om skriptet Blockets längd överskrider vad ETW klarar av anläggning i en enda händelse, delar Windows PowerShell-skriptet i flera delar. Här är exempelkod för att kombinera ett skript från dess loggmeddelanden:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Precis som med alla loggningssystem som har en begränsad kvarhållning buffert (d.v.s. ETW-loggar) är ett angrepp mot den här infrastrukturen att göra loggen med falska händelser att dölja tidigare bevis. Om du vill skydda dig mot angrepp, kontrollera att du har någon form av händelseloggen samling konfigurera (t.ex, Windows vidarebefordran av händelser, [upptäcka angriparen med övervakning av Windows-händelseloggen](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) att flytta händelseloggar från datorn som snart som möjligt.
