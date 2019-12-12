---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Informationsström
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145042"
---
# <a name="information-stream"></a>Informationsström

PowerShell 5,0 lägger till en ny strukturerad **informations** ström för att skicka strukturerade data mellan ett skript och dess värd. `Write-Host` har också uppdaterats för att generera sina utdata till **informations** strömmen där du nu kan fånga eller dämpa den. Den nya `Write-Information`-cmdleten som används med gemensamma parametrar för **InformationVariable** och **InformationAction** ger större flexibilitet och möjlighet.

Följande funktion använder cmdletar som utnyttjar den nya **informations** strömmen.

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

I följande exempel visas resultatet av att köra den här funktionen.

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

`$r`-variabeln har samlat process informationen i skript variabeln `$p`.

```powershell
$r.Id
4008
```

Till skillnad från `Write-Host`-cmdlet: en med hjälp av parametern **InformationVariable** för `Write-Information` kan du avbilda utdata i en variabel. Med hjälp av **taggen**kan du skapa separata kanaler för meddelanden som skickas till **informations** strömmen.

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

När du skickar ett meddelande till **informations** strömmen med en-tagg visas inte meddelandet i värd programmet, men du kan hämta det med hjälp av taggnamnet. Till exempel:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```