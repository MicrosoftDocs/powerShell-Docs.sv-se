---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Skriptspårning och -loggning
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856156"
---
# <a name="script-tracing-and-logging"></a>Skriptspårning och -loggning

Medan PowerShell har redan den **LogPipelineExecutionDetails** grupprinciper för att ställa in logga av cmdlet: ar, PowerShell-skriptspråket har flera funktioner som du kan logga in och granska. Den nya funktionen för detaljerad spårning av skriptet ger detaljerad spårning och analys av PowerShell-skript-aktivitet på ett system. När du har aktiverat detaljerad skriptet spårning PowerShell loggar alla skriptblocken händelseloggen ETW **Microsoft-Windows-PowerShell/Operational**. Om ett skriptblock skapar en annan skriptblocket, till exempel genom att anropa `Invoke-Expression`, anropade skriptblocket även.

Loggning är aktiverat via den **aktiverar loggning för PowerShell-skript Block** gruppolicy-inställningen i **Administrationsmallar** -> **Windows-komponenter**  ->  **Windows PowerShell**.

Händelserna är:

| Kanal |                               Operativa                               |
| ------- | ----------------------------------------------------------------------- |
| Nivå   | Verbose                                                                 |
| OpCode  | Create                                                                  |
| Uppgift    | CommandStart                                                            |
| Nyckelord | körningsutrymme                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Meddelande | Skapa Scriptblock text (%1% 2): </br> %3 </br> ScriptBlock ID: %4 |


Den text som bifogas i meddelandet är omfattningen av skriptblocket kompileras. ID: T är ett GUID som finns kvar för resten av skriptblocket.

När du aktiverar utförlig loggning kan funktionen skrivningar börja och sluta markörer:

| Kanal |                                 Operativa                                |
| ------- | -------------------------------------------------------------------------- |
| Nivå   | Verbose                                                                    |
| OpCode  | Öppna / Stäng                                                               |
| Uppgift    | CommandStart / CommandStop                                                 |
| Nyckelord | körningsutrymme                                                                   |
| EventId | ScriptBlock\_anropa\_starta\_detalj (0x1009 = 4105) / </br> ScriptBlock\_anropa\_fullständig\_detalj (0x100A = 4106) |
| Meddelande | Igång / slutfört anrop av ScriptBlock-ID: %1 </br> Runspace ID: %2 |

ID: T är GUID som representerar skriptblocket (som kan korreleras med händelse-ID 0x1008) och Körningsutrymme-ID representerar runspace där skriptblocket kördes.

Procenttecken i anrop meddelandet representerar strukturerade ETW-egenskaper. När de ersätts med de faktiska värdena i meddelandetexten, ett mer robust sätt att komma åt dem är att hämta meddelandet med cmdleten Get-WinEvent och sedan använda den **egenskaper** matris med meddelandet.

Här är ett exempel på hur den här funktionen kan hjälpa dig att packa upp angripare att kryptera och Förvräng ett skript:

```powershell
## Malware
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

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

Kör detta genererar följande loggposter:

```Output
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

Om skriptet Blockets längd överskrider kapaciteten för en enskild händelse, delar PowerShell-skriptet i flera delar. Här är exempelkod för att kombinera ett skript från dess loggmeddelanden:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Precis som med alla loggningssystem som har en begränsad kvarhållning buffert, är ett sätt att attackera denna infrastruktur att göra loggen med falska händelser att dölja tidigare bevis. Se till att du har någon form av händelseloggen samling konfigurera vidarebefordran av Windows-händelser för att skydda dig mot angrepp. Mer information finns i [upptäcka angriparen med övervakning av Windows-händelseloggen](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).