---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
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