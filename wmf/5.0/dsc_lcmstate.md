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
# <a name="detailed-information-about-lcm-state"></a>Detaljerad information om MGM tillstånd

Vi har gjort förbättringar i exponera information om det MGM. LCMState som returneras av Get-DscLocalConfigurationManager innehåller nu följande värden:

* **Inaktiv**
* **Upptagen**
* **PendingReboot**
* **PendingConfiguration**

Vi har lagt till en LCMStateDetail-egenskap som innehåller mer information om tillståndet.

