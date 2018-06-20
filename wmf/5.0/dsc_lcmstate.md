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
# <a name="detailed-information-about-lcm-state"></a>Detaljerad information om MGM tillstånd

Vi har gjort förbättringar i exponera information om det MGM. LCMState som returneras av Get-DscLocalConfigurationManager innehåller nu följande värden:

* **Inaktiv**
* **Upptagen**
* **PendingReboot**
* **PendingConfiguration**

Vi har lagt till en LCMStateDetail-egenskap som innehåller mer information om tillståndet.
