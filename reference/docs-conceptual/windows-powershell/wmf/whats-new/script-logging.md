---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Skriptspårning och -loggning
ms.openlocfilehash: dd18453c041428d5a6537c413c3ebe324a62dfee
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811200"
---
# <a name="script-tracing-and-logging"></a>Skriptspårning och -loggning

Även om PowerShell redan har inställningen **LogPipelineExecutionDetails** grupprincip för att logga anropet av cmdlets, har PowerShell: s skript språk flera funktioner som du kanske vill logga och granska. Den nya detaljerade skript spårnings funktionen ger detaljerad spårning och analys av PowerShell-skript aktivitet på ett system. När du har aktiverat detaljerad skript spårning loggar PowerShell alla skript block till ETW-händelseloggen, **Microsoft-Windows-PowerShell/Operational**. Om ett skript block skapar ett annat skript block, till exempel genom `Invoke-Expression` att anropa, loggas även det anropade skript blocket.

Loggning har Aktiver ATS med inställningen **Aktivera PowerShell-skript block loggning** Grupprincip i **administrativa mallar**  ->  **Windows-komponenter**  ->  **Windows PowerShell**.

Händelserna är:

| Kanal |                               Verksamhetsrelaterade                               |
| ------- | ----------------------------------------------------------------------- |
| Nivå   | Verbose                                                                 |
| Opcode  | Skapa                                                                  |
| Uppgift    | CommandStart                                                            |
| Följt | Körnings utrymme                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Meddelande | Skapar script block-text (%1 av %2): </br> %3 </br> Script block-ID: %4 |

Texten som är inbäddad i meddelandet är den kompilerade skript blockets omfattning. ID är ett GUID som behålls för skript blockets livs längd.

När du aktiverar utförlig loggning skriver funktionen start-och slut markörer:

| Kanal |                                 Verksamhetsrelaterade                                |
| ------- | -------------------------------------------------------------------------- |
| Nivå   | Verbose                                                                    |
| Opcode  | Öppna/Stäng                                                               |
| Uppgift    | CommandStart / CommandStop                                                 |
| Följt | Körnings utrymme                                                                   |
| EventId | \_Start information för script block Invoke \_ \_ (0x1009 = 4105)/ </br> Script block \_ anropa \_ fullständig \_ detalj (0x100A = 4106) |
| Meddelande | Startade/slutfört anrop av script block-ID: %1 </br> Körnings utrymme-ID: %2 |

ID: t är det GUID som representerar skript blocket (som kan korreleras med händelse-ID 0x1008) och körnings utrymme-ID: t representerar den körnings utrymme som det här skript blocket kördes i.

Procent tecken i anrops meddelandet representerar strukturerade ETW-egenskaper. Medan de ersätts med de faktiska värdena i meddelande texten, är ett mer robust sätt att komma åt dem att hämta meddelandet med cmdleten Get-WinEvent och sedan använda meddelandets **egenskaps** mat ris.

Här är ett exempel på hur den här funktionen kan hjälpa dig att packa upp ett skadligt försök att kryptera och obfuscate ett skript:

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

Om du kör detta genereras följande logg poster:

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

Om skript blockets längd överskrider kapaciteten för en enskild händelse, bryter PowerShell skriptet till flera delar. Här är exempel kod för att kombinera ett skript från dess logg meddelanden:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Precis som med alla loggnings system som har en begränsad kvarhållning, är ett sätt att attackera den här infrastrukturen att överbelasta loggen med spurious-händelser för att dölja tidigare bevis. Om du vill skydda dig från den här angreppet måste du se till att du har en viss typ av händelse logg samling konfigurera vidarebefordring av Windows-händelser. Mer information finns i [upptäcka angripare med Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).
