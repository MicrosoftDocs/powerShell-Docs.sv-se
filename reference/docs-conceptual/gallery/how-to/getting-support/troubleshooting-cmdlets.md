---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Felsöka cmdletar
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329052"
---
# <a name="troubleshooting-cmdlets"></a>Felsöka cmdletar

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Så här löser du "Varning: Paketet "ditt paket namn" kunde inte ladda ned "problem

Det rapporteras att `Install-Module` eller `Update-Module` ibland Miss lyckas på vissa datorer.
Utifrån vår undersökning är det något att göra med nätverks anslutningen.
Vi har nyligen uppdaterat NuGet-leverantören så att den kan ladda ned paket på ett tillförlitligt sätt.
Du kan följa anvisningarna nedan om du vill installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera modulen.
Vi använder Azure-modulen som ett exempel nedan.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
