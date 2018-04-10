---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="f16ed-102">Detaljerad information om MGM tillstånd</span><span class="sxs-lookup"><span data-stu-id="f16ed-102">Detailed information about LCM state</span></span>

<span data-ttu-id="f16ed-103">Vi har gjort förbättringar i exponera information om det MGM.</span><span class="sxs-lookup"><span data-stu-id="f16ed-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="f16ed-104">LCMState som returneras av Get-DscLocalConfigurationManager innehåller nu följande värden:</span><span class="sxs-lookup"><span data-stu-id="f16ed-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="f16ed-105">**Inaktiv**</span><span class="sxs-lookup"><span data-stu-id="f16ed-105">**Idle**</span></span>
* <span data-ttu-id="f16ed-106">**Upptagen**</span><span class="sxs-lookup"><span data-stu-id="f16ed-106">**Busy**</span></span>
* <span data-ttu-id="f16ed-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="f16ed-107">**PendingReboot**</span></span>
* <span data-ttu-id="f16ed-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f16ed-108">**PendingConfiguration**</span></span>

<span data-ttu-id="f16ed-109">Vi har lagt till en LCMStateDetail-egenskap som innehåller mer information om tillståndet.</span><span class="sxs-lookup"><span data-stu-id="f16ed-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>