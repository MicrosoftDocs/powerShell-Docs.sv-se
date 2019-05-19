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
# <a name="information-stream"></a><span data-ttu-id="4fca0-103">Informationsström</span><span class="sxs-lookup"><span data-stu-id="4fca0-103">Information Stream</span></span>

<span data-ttu-id="4fca0-104">PowerShell 5.0 lägger till en ny strukturerade **Information** stream sända strukturerade data mellan ett skript och dess värd.</span><span class="sxs-lookup"><span data-stu-id="4fca0-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="4fca0-105">`Write-Host` har också uppdaterats för att generera dess utdata till den **Information** stream där du kan nu avbilda eller inaktivera den.</span><span class="sxs-lookup"><span data-stu-id="4fca0-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="4fca0-106">Den nya `Write-Information` cmdlet som används med **InformationVariable** och **InformationAction** gemensamma parametrar möjliggör mer flexibilitet och funktion.</span><span class="sxs-lookup"><span data-stu-id="4fca0-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="4fca0-107">Följande funktion använder cmdlet: ar som drar nytta av den nya **Information** stream.</span><span class="sxs-lookup"><span data-stu-id="4fca0-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="4fca0-108">I följande exempel visar resultaten för att köra den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="4fca0-108">The following examples show the results of running this function.</span></span>

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

<span data-ttu-id="4fca0-109">Den `$r` variabeln har hämtats av processinformation i variabeln skriptet `$p`.</span><span class="sxs-lookup"><span data-stu-id="4fca0-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="4fca0-110">Till skillnad från den `Write-Host` cmdlet, med hjälp av den **InformationVariable** -parametern för `Write-Information` kan du avbilda utdata i en variabel.</span><span class="sxs-lookup"><span data-stu-id="4fca0-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="4fca0-111">Med hjälp av den **taggen**, du kan skapa separata kanaler för meddelanden som skickas till den **Information** stream.</span><span class="sxs-lookup"><span data-stu-id="4fca0-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="4fca0-112">När du skickar ett meddelande till den **Information** ström med en tagg, meddelandet inte visas i värdprogrammet men kan hämtas med hjälp av taggnamnet.</span><span class="sxs-lookup"><span data-stu-id="4fca0-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="4fca0-113">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fca0-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```