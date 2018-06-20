---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: 'Felsökning av cmdlet: ar'
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219835"
---
# <a name="troubleshooting-cmdlets"></a>Felsökning av cmdlet: ar

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Så här löser du ”varning: Det gick inte att hämta paketet ditt paketnamn” problemet?

Det har rapporterats att installera modulen eller Update-Module Ibland misslyckas på vissa datorer.
Baserat på våra undersökningar, är det att göra med nätverksanslutningen.
Vi uppdaterade nyligen NuGet-providern så att den kan hämta paket på ett tillförlitligt sätt.
Här följer du anvisningarna nedan för att installera den senaste versionen av providern NuGet och sedan installera eller uppdatera din modul.
Nu ska vi använda 'Azure-modulen som exemplet nedan.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```