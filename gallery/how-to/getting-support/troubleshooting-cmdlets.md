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
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="3e3bd-103">Felsökning av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="3e3bd-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="3e3bd-104">Så här löser du ”varning: Det gick inte att hämta paketet ditt paketnamn” problemet?</span><span class="sxs-lookup"><span data-stu-id="3e3bd-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="3e3bd-105">Det har rapporterats att installera modulen eller Update-Module Ibland misslyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="3e3bd-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="3e3bd-106">Baserat på våra undersökningar, är det att göra med nätverksanslutningen.</span><span class="sxs-lookup"><span data-stu-id="3e3bd-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="3e3bd-107">Vi uppdaterade nyligen NuGet-providern så att den kan hämta paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="3e3bd-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="3e3bd-108">Här följer du anvisningarna nedan för att installera den senaste versionen av providern NuGet och sedan installera eller uppdatera din modul.</span><span class="sxs-lookup"><span data-stu-id="3e3bd-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="3e3bd-109">Nu ska vi använda 'Azure-modulen som exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="3e3bd-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```