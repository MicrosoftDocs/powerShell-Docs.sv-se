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
# <a name="detailed-information-about-lcm-state"></a>Detaljerad information om LCM-tillstånd

Vi har gjort förbättringar i exponera information om LCM-tillstånd. LCMState som returneras av Get-DscLocalConfigurationManager kan nu ha följande värden:

* **Inaktiv**
* **Upptagen**
* **PendingReboot**
* **PendingConfiguration**

Vi har också lagt till en LCMStateDetail-egenskap som innehåller mer information om tillstånd.
