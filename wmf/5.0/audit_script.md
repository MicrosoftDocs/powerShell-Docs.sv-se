---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 2c3cc6d5d226daf22c7ee83a1b7068d6a08b7f45
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="script-tracing-and-logging"></a>Skriptet spårning och loggning

Även om Windows PowerShell har redan den **LogPipelineExecutionDetails** Grupprincip inställningen logga anrop av cmdlets PowerShells skriptspråk har tillräckligt med funktioner som du kanske vill logga in och/eller granska. Den nya funktionen för spårning av detaljerad skript kan du aktivera detaljerad spårning och analys av Windows PowerShell scripting används på ett system. När du aktiverar spårning detaljerat skript, Windows PowerShell loggar alla skriptblock händelseloggen ETW **Microsoft-Windows-PowerShell/Operational**. Om ett skriptblock skapar ett annat skriptblock (till exempel ett skript som anropar cmdleten Invoke-Expression på en sträng), loggas samt det resulterande skriptblocket.

Loggning av dessa händelser kan aktiveras via den **aktiverar du loggning för PowerShell-skript Block** grupprincipinställningen (i Administrationsmallar -> Windows-komponenter -> Windows PowerShell).

Händelser är:

| Kanal | Använd                                 |
|---------|---------------------------------------------|
| Nivå   | Verbose                                     |
| OpCode  | Create                                      |
| Uppgift    | CommandStart                                |
| Nyckelordet | Runspace                                    |
| Händelse-ID | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Meddelande | Skapa Scriptblock text (%1% 2): </br> %3 </br> ScriptBlock-ID: %4 |


Den text som bifogas i meddelandet är omfattningen av skriptblocket kompileras. ID: T är ett GUID som sparas i skriptblocket livslängd.

När du aktiverar utförlig loggning funktionen skrivningar börja och sluta markörer:

| Kanal | Använd                                            |
|---------|--------------------------------------------------------|
| Nivå   | Verbose                                                |
| OpCode  | Öppna (/ Stäng)                                         |
| Uppgift    | CommandStart (/ CommandStop)                           |
| Nyckelordet | Runspace                                               |
| Händelse-ID | ScriptBlock\_anropa\_starta\_detalj (0x1009 = 4105) / </br> ScriptBlock\_anropa\_fullständig\_detalj (0x100A = 4106) |
| Meddelande | Igång (/ slutförda) anrop av ScriptBlock-ID: %1 </br> Runspace-ID: %2 |

ID: T är GUID som representerar skriptblocket (som kan korreleras med händelse-ID 0x1008) och Runspace ID representerar runspace där skriptblocket kördes.

Procenttecken i anrops-meddelandet representerar strukturerade ETW-egenskaper. När de ersätts med de faktiska värdena i meddelandetexten är ett mer stabilt sätt att komma åt dem att hämta meddelandet med cmdleten Get-WinEvent och sedan använda den **egenskaper** matris med meddelandet.

Här är ett exempel på hur den här funktionen kan hjälpa dig att packa angripare att kryptera och obfuscate ett skript:

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

Om skriptet Blockets längd överskrider vad ETW kan anläggning i en enskild händelse, delar skriptet i flera delar i Windows PowerShell. Här är exempelkod som sätter ett skript från dess loggmeddelanden:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Precis som med alla loggning system som har en begränsad kvarhållning buffert (d.v.s. ETW-loggarna) är en attack mot denna infrastruktur att översvämma logg med falska händelser att dölja tidigare bevis. Om du vill skydda dig mot angrepp, kontrollera att du har någon form av händelseloggen samling konfigurera (d.v.s. händelse vidarebefordran av Windows, [upptäcka angriparen med övervakning av Windows händelselogg](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) att flytta loggar ut från datorn som snart som möjligt.

