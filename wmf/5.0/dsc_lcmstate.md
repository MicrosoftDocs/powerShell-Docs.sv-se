---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="01b96-102">Detaljerad information om MGM tillstånd</span><span class="sxs-lookup"><span data-stu-id="01b96-102">Detailed information about LCM state</span></span>

<span data-ttu-id="01b96-103">Vi har gjort förbättringar i exponera information om det MGM.</span><span class="sxs-lookup"><span data-stu-id="01b96-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="01b96-104">LCMState som returneras av Get-DscLocalConfigurationManager innehåller nu följande värden:</span><span class="sxs-lookup"><span data-stu-id="01b96-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="01b96-105">**Inaktiv**</span><span class="sxs-lookup"><span data-stu-id="01b96-105">**Idle**</span></span>
* <span data-ttu-id="01b96-106">**Upptagen**</span><span class="sxs-lookup"><span data-stu-id="01b96-106">**Busy**</span></span>
* <span data-ttu-id="01b96-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="01b96-107">**PendingReboot**</span></span>
* <span data-ttu-id="01b96-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="01b96-108">**PendingConfiguration**</span></span>

<span data-ttu-id="01b96-109">Vi har lagt till en LCMStateDetail-egenskap som innehåller mer information om tillståndet.</span><span class="sxs-lookup"><span data-stu-id="01b96-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

