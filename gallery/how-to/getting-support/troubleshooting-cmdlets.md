---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: 'Felsökning av cmdlet: ar'
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
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