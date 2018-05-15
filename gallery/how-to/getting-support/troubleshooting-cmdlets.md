---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: 'Felsökning av cmdlet: ar'
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="e230c-103">Felsökning av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="e230c-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="e230c-104">Så här löser du ”varning: Det gick inte att hämta paketet ditt paketnamn” problemet?</span><span class="sxs-lookup"><span data-stu-id="e230c-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="e230c-105">Det har rapporterats att installera modulen eller Update-Module Ibland misslyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="e230c-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="e230c-106">Baserat på våra undersökningar, är det att göra med nätverksanslutningen.</span><span class="sxs-lookup"><span data-stu-id="e230c-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="e230c-107">Vi uppdaterade nyligen NuGet-providern så att den kan hämta paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="e230c-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="e230c-108">Här följer du anvisningarna nedan för att installera den senaste versionen av providern NuGet och sedan installera eller uppdatera din modul.</span><span class="sxs-lookup"><span data-stu-id="e230c-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="e230c-109">Nu ska vi använda 'Azure-modulen som exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="e230c-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```