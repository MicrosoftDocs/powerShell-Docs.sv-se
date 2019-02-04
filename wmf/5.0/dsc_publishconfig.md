---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684509"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Leverera en konfigurationsdokumentet utan att tillämpa

Den [publicera-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet kopierar en MOF-konfigurationsfilen till en målnod, men gäller inte konfigurationen.
Den här konfigurationen tillämpas under nästa konsekvens passet eller när du kör den [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.
