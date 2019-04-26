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
# <a name="detailed-information-about-lcm-state"></a>Detaljerad information om LCM-tillstånd

Vi har gjort förbättringar i exponera information om LCM-tillstånd. LCMState som returneras av Get-DscLocalConfigurationManager kan nu ha följande värden:

* **Inaktiv**
* **Upptagen**
* **PendingReboot**
* **PendingConfiguration**

Vi har också lagt till en LCMStateDetail-egenskap som innehåller mer information om tillstånd.
