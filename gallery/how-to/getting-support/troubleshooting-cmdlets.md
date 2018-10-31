---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: 'Felsökning av cmdlet: ar'
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002470"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="3cc20-103">Felsökning av cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="3cc20-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="3cc20-104">Så här löser du ”varning: paketet ditt paketnamn kunde inte hämta” problem</span><span class="sxs-lookup"><span data-stu-id="3cc20-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="3cc20-105">Rapporteras den som `Install-Module` eller `Update-Module` Ibland misslyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="3cc20-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="3cc20-106">Baserat på vår undersökning, är det att göra med nätverksanslutningen.</span><span class="sxs-lookup"><span data-stu-id="3cc20-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="3cc20-107">Nyligen har uppdaterat vi NuGet-providern så att den kan hämta paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="3cc20-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="3cc20-108">Du kan följa anvisningarna nedan för att installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera din modul.</span><span class="sxs-lookup"><span data-stu-id="3cc20-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="3cc20-109">Nu ska vi använda ”Azure”-modulen som exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="3cc20-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
