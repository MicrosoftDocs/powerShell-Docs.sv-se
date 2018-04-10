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
# <a name="detailed-information-about-lcm-state"></a>Detaljerad information om MGM tillstånd

Vi har gjort förbättringar i exponera information om det MGM. LCMState som returneras av Get-DscLocalConfigurationManager innehåller nu följande värden:

* **Inaktiv**
* **Upptagen**
* **PendingReboot**
* **PendingConfiguration**

Vi har lagt till en LCMStateDetail-egenskap som innehåller mer information om tillståndet.