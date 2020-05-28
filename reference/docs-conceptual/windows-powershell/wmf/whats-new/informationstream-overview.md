---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Informationsström
ms.openlocfilehash: 39cb3c36a70530b3ff9777edc74b88d276cbbb7c
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810374"
---
# <a name="information-stream"></a>Informationsström

PowerShell 5,0 lägger till en ny strukturerad **informations** ström för att skicka strukturerade data mellan ett skript och dess värd. `Write-Host`har också uppdaterats för att skicka utdata till **informations** strömmen där du nu kan fånga eller dämpa den. Den nya `Write-Information` cmdleten som används med **InformationVariable** och **InformationAction** vanliga parametrar möjliggör större flexibilitet och kapacitet.

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

`$r`Variabeln har samlat in process informationen i skript variabeln `$p` .

```powershell
$r.Id
4008
```

Till skillnad från `Write-Host` -cmdlet: en **InformationVariable** med parametern InformationVariable `Write-Information` kan du avbilda utdata i en variabel. Med hjälp av **taggen**kan du skapa separata kanaler för meddelanden som skickas till **informations** strömmen.

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

När du skickar ett meddelande till **informations** strömmen med en-tagg visas inte meddelandet i värd programmet, men du kan hämta det med hjälp av taggnamnet. Ett exempel:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```