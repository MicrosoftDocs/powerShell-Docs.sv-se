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
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="c12a6-103">Så här löser du ”varning: Det gick inte att hämta paketet ditt paketnamn” problemet?</span><span class="sxs-lookup"><span data-stu-id="c12a6-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="c12a6-104">Det har rapporterats att installera modulen eller Update-Module Ibland misslyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="c12a6-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="c12a6-105">Baserat på våra undersökningar, är det att göra med nätverksanslutningen.</span><span class="sxs-lookup"><span data-stu-id="c12a6-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="c12a6-106">Vi uppdaterade nyligen NuGet-providern så att den kan hämta paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="c12a6-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="c12a6-107">Här följer du anvisningarna nedan för att installera den senaste versionen av providern NuGet och sedan installera eller uppdatera din modul.</span><span class="sxs-lookup"><span data-stu-id="c12a6-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="c12a6-108">Nu ska vi använda 'Azure-modulen som exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="c12a6-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```