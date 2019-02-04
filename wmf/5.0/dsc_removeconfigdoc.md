---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: eec82b0cb9860d07a282a07c414c3723be313fa4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683760"
---
# <a name="remove-dsc-documents"></a>Ta bort DSC-dokument

När en konfigurationsdokumentet levereras till DSC, går dokumentet igenom olika faser (väntande, aktuella, tidigare). Vi har lagt till en ny cmdlet i DSC i Windows PowerShell 4.0 `Remove-DscConfigurationDocument`, som en del av [November 2014-uppdatering för Windows RT 8.1, Windows 8.1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850).
