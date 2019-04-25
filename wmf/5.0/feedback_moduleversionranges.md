---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057520"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Modulstöd för att deklarera versionsintervall (1.*, osv)
I kombination med **- MinimumVersion**, **- MaximumVersion** nu tillåter användare att get/import-module inom specifika intervall. Parametern stöder också **.** \*. I följande exempel visas hur det fungerar:

Nu, kan du kombinera **- MinimumVersion** och **- MaximumVersion** importera modul inom specifika intervall:

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
