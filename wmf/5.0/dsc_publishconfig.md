---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Leverera ett konfigurationsdokument av utan att använda

Den [publicera DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet kopierar en konfiguration MOF-fil till en målnod, men inte tillämpa konfigurationen.
Den här konfigurationen används under nästa konsekvenskontroll steget, eller när du kör den [uppdatering DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.
