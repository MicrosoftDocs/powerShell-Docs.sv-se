---
ms.date: 06/12/2017
title: Informationsström
description: PowerShell 5,0 lägger till en ny strukturerad **informations** ström för att skicka strukturerade data mellan ett skript och dess värd.
ms.openlocfilehash: 818c99ce281f5ada596ff92cd7bafb8b7cacf709
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646708"
---
# <a name="information-stream"></a><span data-ttu-id="de060-103">Informationsström</span><span class="sxs-lookup"><span data-stu-id="de060-103">Information Stream</span></span>

<span data-ttu-id="de060-104">PowerShell 5,0 lägger till en ny strukturerad **informations** ström för att skicka strukturerade data mellan ett skript och dess värd.</span><span class="sxs-lookup"><span data-stu-id="de060-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="de060-105">`Write-Host` har också uppdaterats för att skicka utdata till **informations** strömmen där du nu kan fånga eller dämpa den.</span><span class="sxs-lookup"><span data-stu-id="de060-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="de060-106">Den nya `Write-Information` cmdleten som används med **InformationVariable** och **InformationAction** vanliga parametrar möjliggör större flexibilitet och kapacitet.</span><span class="sxs-lookup"><span data-stu-id="de060-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="de060-107">Följande funktion använder cmdletar som utnyttjar den nya **informations** strömmen.</span><span class="sxs-lookup"><span data-stu-id="de060-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="de060-108">I följande exempel visas resultatet av att köra den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="de060-108">The following examples show the results of running this function.</span></span>

```powershell
$r = OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="de060-109">`$r`Variabeln har samlat in process informationen i skript variabeln `$p` .</span><span class="sxs-lookup"><span data-stu-id="de060-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="de060-110">Till skillnad från `Write-Host` -cmdlet: en **InformationVariable** med parametern InformationVariable `Write-Information` kan du avbilda utdata i en variabel.</span><span class="sxs-lookup"><span data-stu-id="de060-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="de060-111">Med hjälp av **taggen** kan du skapa separata kanaler för meddelanden som skickas till **informations** strömmen.</span><span class="sxs-lookup"><span data-stu-id="de060-111">Using the **Tag** , you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="de060-112">När du skickar ett meddelande till **informations** strömmen med en-tagg visas inte meddelandet i värd programmet, men du kan hämta det med hjälp av taggnamnet.</span><span class="sxs-lookup"><span data-stu-id="de060-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="de060-113">Exempel:</span><span class="sxs-lookup"><span data-stu-id="de060-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
