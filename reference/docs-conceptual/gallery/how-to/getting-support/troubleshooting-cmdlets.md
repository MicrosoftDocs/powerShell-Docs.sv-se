---
ms.date: 01/25/2021
title: Felsöka cmdletar
description: Den här artikeln innehåller information och anvisningar för fel sökning av fel med hjälp av PowerShell-galleriet
ms.openlocfilehash: 8139147683b655b5f8532c3068387db6df12a98f
ms.sourcegitcommit: 0f003644684422e425a59b7361121e05ac772e15
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98771808"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="cb3bb-103">Felsöka cmdletar</span><span class="sxs-lookup"><span data-stu-id="cb3bb-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="cb3bb-104">Så här löser du "varning! Package" ditt paket namn "Det gick inte att ladda ned" problem</span><span class="sxs-lookup"><span data-stu-id="cb3bb-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="cb3bb-105">Det rapporteras att `Install-Module` eller `Update-Module` ibland Miss lyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="cb3bb-106">Utifrån vår undersökning är det något att göra med nätverks anslutningen.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="cb3bb-107">Vi har nyligen uppdaterat NuGet-leverantören så att den kan ladda ned paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="cb3bb-108">Du kan följa anvisningarna nedan om du vill installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera modulen.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="cb3bb-109">Vi använder Azure-modulen som ett exempel nedan.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a><span data-ttu-id="cb3bb-110">Nätverks slut punkter som krävs</span><span class="sxs-lookup"><span data-stu-id="cb3bb-110">Required network endpoints</span></span>

<span data-ttu-id="cb3bb-111">Installations-och uppdaterings-cmdletarna kräver Internet åtkomst för att ansluta till de nätverks slut punkter som används av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="cb3bb-112">Kontrol lera att nätverks åtkomst principerna tillåter att du ansluter till följande slut punkter.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="cb3bb-113">`psg-prod-eastus.azureedge.net` -CDN-värdnamn</span><span class="sxs-lookup"><span data-stu-id="cb3bb-113">`psg-prod-eastus.azureedge.net` - CDN hostname</span></span>
- <span data-ttu-id="cb3bb-114">`az818661.vo.msecnd.net` -CDN-värdnamn</span><span class="sxs-lookup"><span data-stu-id="cb3bb-114">`az818661.vo.msecnd.net` - CDN hostname</span></span>
- <span data-ttu-id="cb3bb-115">`devopsgallerystorage.blob.core.windows.net` -lagrings kontots värdnamn</span><span class="sxs-lookup"><span data-stu-id="cb3bb-115">`devopsgallerystorage.blob.core.windows.net` - storage account hostname</span></span>
- <span data-ttu-id="cb3bb-116">`*.powershellgallery.com` – webbplats</span><span class="sxs-lookup"><span data-stu-id="cb3bb-116">`*.powershellgallery.com` - website</span></span>
- <span data-ttu-id="cb3bb-117">`go.microsoft.com` – omdirigerings tjänst</span><span class="sxs-lookup"><span data-stu-id="cb3bb-117">`go.microsoft.com` - redirection service</span></span>
- <span data-ttu-id="cb3bb-118">`onegetcdn.azureedge.net` – Bootstrap NuGet-providern i `PowerShellGet/PackageManagement`</span><span class="sxs-lookup"><span data-stu-id="cb3bb-118">`onegetcdn.azureedge.net` - bootstrap the NuGet Provider in `PowerShellGet/PackageManagement`</span></span>

> [!NOTE]
> <span data-ttu-id="cb3bb-119">Cmdletar som interagerar med PowerShell-galleriet kan inte utföras med oväntade fel när PowerShell-galleriet tjänsterna har avbrottit.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-119">Cmdlets that interact with the PowerShell Gallery can fail with unexpected errors when there is an outage of the PowerShell Gallery services.</span></span> <span data-ttu-id="cb3bb-120">Om du vill se PowerShell-gallerietens aktuella status går du till sidan [PowerShell-galleriet status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) på GitHub.</span><span class="sxs-lookup"><span data-stu-id="cb3bb-120">To see the current status of the PowerShell Gallery, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>
