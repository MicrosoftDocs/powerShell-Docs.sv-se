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
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="b4bf0-103">Nyheter i PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="b4bf0-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="b4bf0-104">Nedan visas ett urval av några av de nya funktioner och ändringar som har införts i PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="b4bf0-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="b4bf0-105">Det finns också **ton** av ”tråkiga” som gör att PowerShell snabbare och mer tillförlitliga (plus utbudet felkorrigeringar)!</span><span class="sxs-lookup"><span data-stu-id="b4bf0-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="b4bf0-106">En fullständig lista över ändringar, Kolla in vår [ändringsloggen på GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="b4bf0-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="b4bf0-107">Och medan vi anropa vissa namn nedan tack till [alla community-deltagare](https://github.com/PowerShell/PowerShell/graphs/contributors) som möjligt den här versionen.</span><span class="sxs-lookup"><span data-stu-id="b4bf0-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="b4bf0-108">Uppdateringar och korrigeringar</span><span class="sxs-lookup"><span data-stu-id="b4bf0-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="b4bf0-109">Lägg till PowerShell-fjärrkommunikation aktivera/inaktivera cmdlet varningsmeddelanden ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="b4bf0-110">Korrigering för `FormatTable` remote deserialisering regression ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="b4bf0-111">Uppdatera den uppgiftsbaserade `async` API: er som har lagts till i PowerShell för att returnera ett aktivitetsobjekt direkt ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="b4bf0-112">Lägg till 5 `InvokeAsync` överlagringar och `StopAsync` till den `PowerShell` typ ([#8056][]) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="b4bf0-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="b4bf0-113">Allmänna Cmdlet uppdateringar och korrigeringar</span><span class="sxs-lookup"><span data-stu-id="b4bf0-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="b4bf0-114">Aktivera `SecureString` -cmdletar för Windows genom att lagra den oformaterade texten ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="b4bf0-115">Lägg till föråldrat meddelande till `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="b4bf0-116">Åtgärda `Restart-Computer` att arbeta med `localhost` när WinRM finns inte ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="b4bf0-117">Kontrollera `Start-Job` throw avslutande fel när PowerShell finns ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="b4bf0-118">Uppdateringsversion för `PowerShell.Native` och som är värd för tester ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="b4bf0-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="b4bf0-119">Icke-bakåtkompatibla ändringar</span><span class="sxs-lookup"><span data-stu-id="b4bf0-119">Breaking Changes</span></span>

<span data-ttu-id="b4bf0-120">Åtgärda - NoEnumerate beteende i Write-Output för att överensstämma med Windows PowerShell ([#9069][]) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="b4bf0-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

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
