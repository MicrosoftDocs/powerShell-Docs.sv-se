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
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="63c64-103">Felsöka cmdletar</span><span class="sxs-lookup"><span data-stu-id="63c64-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="63c64-104">Så här löser du "Varning: Paketet "ditt paket namn" kunde inte ladda ned "problem</span><span class="sxs-lookup"><span data-stu-id="63c64-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="63c64-105">Det rapporteras att `Install-Module` eller `Update-Module` ibland Miss lyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="63c64-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="63c64-106">Utifrån vår undersökning är det något att göra med nätverks anslutningen.</span><span class="sxs-lookup"><span data-stu-id="63c64-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="63c64-107">Vi har nyligen uppdaterat NuGet-leverantören så att den kan ladda ned paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="63c64-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="63c64-108">Du kan följa anvisningarna nedan om du vill installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera modulen.</span><span class="sxs-lookup"><span data-stu-id="63c64-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="63c64-109">Vi använder Azure-modulen som ett exempel nedan.</span><span class="sxs-lookup"><span data-stu-id="63c64-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
