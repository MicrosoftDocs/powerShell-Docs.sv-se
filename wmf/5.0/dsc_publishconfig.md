---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085821"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Leverera en konfigurationsdokumentet utan att tillämpa

Den [publicera-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet kopierar en MOF-konfigurationsfilen till en målnod, men gäller inte konfigurationen.
Den här konfigurationen tillämpas under nästa konsekvens passet eller när du kör den [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.
