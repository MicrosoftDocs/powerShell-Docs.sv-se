---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Informationsström
ms.openlocfilehash: 39cb3c36a70530b3ff9777edc74b88d276cbbb7c
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560125"
---
# <a name="information-stream"></a><span data-ttu-id="8d472-103">Informationsström</span><span class="sxs-lookup"><span data-stu-id="8d472-103">Information Stream</span></span>

<span data-ttu-id="8d472-104">PowerShell 5,0 lägger till en ny strukturerad **informations** ström för att skicka strukturerade data mellan ett skript och dess värd.</span><span class="sxs-lookup"><span data-stu-id="8d472-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="8d472-105">`Write-Host`har också uppdaterats för att skicka utdata till **informations** strömmen där du nu kan fånga eller dämpa den.</span><span class="sxs-lookup"><span data-stu-id="8d472-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="8d472-106">Den nya `Write-Information` cmdleten som används med **InformationVariable** och **InformationAction** vanliga parametrar möjliggör större flexibilitet och kapacitet.</span><span class="sxs-lookup"><span data-stu-id="8d472-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="8d472-107">Följande funktion använder cmdletar som utnyttjar den nya **informations** strömmen.</span><span class="sxs-lookup"><span data-stu-id="8d472-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="8d472-108">I följande exempel visas resultatet av att köra den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="8d472-108">The following examples show the results of running this function.</span></span>

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

<span data-ttu-id="8d472-109">`$r`Variabeln har samlat in process informationen i skript variabeln `$p` .</span><span class="sxs-lookup"><span data-stu-id="8d472-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="8d472-110">Till skillnad från `Write-Host` -cmdlet: en **InformationVariable** med parametern InformationVariable `Write-Information` kan du avbilda utdata i en variabel.</span><span class="sxs-lookup"><span data-stu-id="8d472-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="8d472-111">Med hjälp av **taggen**kan du skapa separata kanaler för meddelanden som skickas till **informations** strömmen.</span><span class="sxs-lookup"><span data-stu-id="8d472-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="8d472-112">När du skickar ett meddelande till **informations** strömmen med en-tagg visas inte meddelandet i värd programmet, men du kan hämta det med hjälp av taggnamnet.</span><span class="sxs-lookup"><span data-stu-id="8d472-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="8d472-113">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="8d472-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
