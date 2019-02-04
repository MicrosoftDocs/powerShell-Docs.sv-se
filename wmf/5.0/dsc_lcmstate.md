---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685748"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="fd238-102">Detaljerad information om LCM-tillstånd</span><span class="sxs-lookup"><span data-stu-id="fd238-102">Detailed information about LCM state</span></span>

<span data-ttu-id="fd238-103">Vi har gjort förbättringar i exponera information om LCM-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fd238-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="fd238-104">LCMState som returneras av Get-DscLocalConfigurationManager kan nu ha följande värden:</span><span class="sxs-lookup"><span data-stu-id="fd238-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="fd238-105">**Inaktiv**</span><span class="sxs-lookup"><span data-stu-id="fd238-105">**Idle**</span></span>
* <span data-ttu-id="fd238-106">**Upptagen**</span><span class="sxs-lookup"><span data-stu-id="fd238-106">**Busy**</span></span>
* <span data-ttu-id="fd238-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="fd238-107">**PendingReboot**</span></span>
* <span data-ttu-id="fd238-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fd238-108">**PendingConfiguration**</span></span>

<span data-ttu-id="fd238-109">Vi har också lagt till en LCMStateDetail-egenskap som innehåller mer information om tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fd238-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
