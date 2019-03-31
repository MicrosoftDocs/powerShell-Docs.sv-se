---
title: Nyheter i PowerShell Core 6.2
description: Nya funktioner och ändringar som introducerades i PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750038"
---
# <a name="whats-new-in-powershell-core-62"></a>Nyheter i PowerShell Core 6.2

Nedan visas ett urval av några av de nya funktioner och ändringar som har införts i PowerShell Core 6.2.

Det finns också **ton** av ”tråkiga” som gör att PowerShell snabbare och mer tillförlitliga (plus utbudet felkorrigeringar)!
En fullständig lista över ändringar, Kolla in vår [ändringsloggen på GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Och medan vi anropa vissa namn nedan tack till [alla community-deltagare](https://github.com/PowerShell/PowerShell/graphs/contributors) som möjligt den här versionen.

## <a name="engine-updates-and-fixes"></a>Uppdateringar och korrigeringar

- Lägg till PowerShell-fjärrkommunikation aktivera/inaktivera cmdlet varningsmeddelanden ([#9203][])
- Korrigering för `FormatTable` remote deserialisering regression ([#9116][])
- Uppdatera den uppgiftsbaserade `async` API: er som har lagts till i PowerShell för att returnera ett aktivitetsobjekt direkt ([#9079][])
- Lägg till 5 `InvokeAsync` överlagringar och `StopAsync` till den `PowerShell` typ ([#8056][]) (tack @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Allmänna Cmdlet uppdateringar och korrigeringar

- Aktivera `SecureString` -cmdletar för Windows genom att lagra den oformaterade texten ([#9199][])
- Lägg till föråldrat meddelande till `Send-MailMessage` ([#9178][])
- Åtgärda `Restart-Computer` att arbeta med `localhost` när WinRM finns inte ([#9160][])
- Kontrollera `Start-Job` throw avslutande fel när PowerShell finns ([#9128][])
- Uppdateringsversion för `PowerShell.Native` och som är värd för tester ([#8983][])

## <a name="breaking-changes"></a>Icke-bakåtkompatibla ändringar

Åtgärda - NoEnumerate beteende i Write-Output för att överensstämma med Windows PowerShell ([#9069][]) (tack @vexx32!)

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
