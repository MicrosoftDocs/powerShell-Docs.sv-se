---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Informationsström
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856387"
---
# <a name="information-stream"></a>Informationsström

PowerShell 5.0 lägger till en ny strukturerade **Information** stream sända strukturerade data mellan ett skript och dess värd. `Write-Host` har också uppdaterats för att generera dess utdata till den **Information** stream där du kan nu avbilda eller inaktivera den. Den nya `Write-Information` cmdlet som används med **InformationVariable** och **InformationAction** gemensamma parametrar möjliggör mer flexibilitet och funktion.

Följande funktion använder cmdlet: ar som drar nytta av den nya **Information** stream.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

I följande exempel visar resultaten för att köra den här funktionen.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

Den `$r` variabeln har hämtats av processinformation i variabeln skriptet `$p`.

```powershell
$r.Id
4008
```

Till skillnad från den `Write-Host` cmdlet, med hjälp av den **InformationVariable** -parametern för `Write-Information` kan du avbilda utdata i en variabel. Med hjälp av den **taggen**, du kan skapa separata kanaler för meddelanden som skickas till den **Information** stream.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

När du skickar ett meddelande till den **Information** ström med en tagg, meddelandet inte visas i värdprogrammet men kan hämtas med hjälp av taggnamnet. Till exempel:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```