---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: 'Felsökning av cmdlet: ar'
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892482"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="24150-103">Felsökning av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="24150-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="24150-104">Så här löser du ”varning: paketet ditt paketnamn kunde inte hämta” problem</span><span class="sxs-lookup"><span data-stu-id="24150-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="24150-105">Rapporteras den som `Install-Module` eller `Update-Module` Ibland misslyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="24150-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="24150-106">Baserat på vår undersökning, är det att göra med nätverksanslutningen.</span><span class="sxs-lookup"><span data-stu-id="24150-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="24150-107">Nyligen har uppdaterat vi NuGet-providern så att den kan hämta paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="24150-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="24150-108">Du kan följa anvisningarna nedan för att installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera din modul.</span><span class="sxs-lookup"><span data-stu-id="24150-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="24150-109">Nu ska vi använda ”Azure”-modulen som exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="24150-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```