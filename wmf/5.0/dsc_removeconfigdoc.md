---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: af16ce7c5d97731581aa3393a70aba672244c9d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="remove-dsc-documents"></a>Ta bort DSC-dokument

När ett dokument configuration levereras till DSC, genomgår dokumentet olika faser (väntande aktuella, tidigare). Vi har lagt till en ny cmdlet i DSC i Windows PowerShell 4.0 `Remove-DscConfigurationDocument`, som en del av [Samlad uppdatering för Windows RT 8.1, Windows 8.1 och Windows Server 2012 R2 i November 2014](https://support.microsoft.com/kb/3000850).
