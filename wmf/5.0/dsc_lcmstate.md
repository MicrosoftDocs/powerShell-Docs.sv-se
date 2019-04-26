---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085804"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="19d6b-102">Detaljerad information om LCM-tillstånd</span><span class="sxs-lookup"><span data-stu-id="19d6b-102">Detailed information about LCM state</span></span>

<span data-ttu-id="19d6b-103">Vi har gjort förbättringar i exponera information om LCM-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="19d6b-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="19d6b-104">LCMState som returneras av Get-DscLocalConfigurationManager kan nu ha följande värden:</span><span class="sxs-lookup"><span data-stu-id="19d6b-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="19d6b-105">**Inaktiv**</span><span class="sxs-lookup"><span data-stu-id="19d6b-105">**Idle**</span></span>
* <span data-ttu-id="19d6b-106">**Upptagen**</span><span class="sxs-lookup"><span data-stu-id="19d6b-106">**Busy**</span></span>
* <span data-ttu-id="19d6b-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="19d6b-107">**PendingReboot**</span></span>
* <span data-ttu-id="19d6b-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="19d6b-108">**PendingConfiguration**</span></span>

<span data-ttu-id="19d6b-109">Vi har också lagt till en LCMStateDetail-egenskap som innehåller mer information om tillstånd.</span><span class="sxs-lookup"><span data-stu-id="19d6b-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
