---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219869"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="c94c6-102">Detaljerad information om MGM tillstånd</span><span class="sxs-lookup"><span data-stu-id="c94c6-102">Detailed information about LCM state</span></span>

<span data-ttu-id="c94c6-103">Vi har gjort förbättringar i exponera information om det MGM.</span><span class="sxs-lookup"><span data-stu-id="c94c6-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="c94c6-104">LCMState som returneras av Get-DscLocalConfigurationManager innehåller nu följande värden:</span><span class="sxs-lookup"><span data-stu-id="c94c6-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="c94c6-105">**Inaktiv**</span><span class="sxs-lookup"><span data-stu-id="c94c6-105">**Idle**</span></span>
* <span data-ttu-id="c94c6-106">**Upptagen**</span><span class="sxs-lookup"><span data-stu-id="c94c6-106">**Busy**</span></span>
* <span data-ttu-id="c94c6-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="c94c6-107">**PendingReboot**</span></span>
* <span data-ttu-id="c94c6-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="c94c6-108">**PendingConfiguration**</span></span>

<span data-ttu-id="c94c6-109">Vi har lagt till en LCMStateDetail-egenskap som innehåller mer information om tillståndet.</span><span class="sxs-lookup"><span data-stu-id="c94c6-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
