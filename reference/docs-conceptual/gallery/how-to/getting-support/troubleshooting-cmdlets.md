---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Felsöka cmdletar
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352116"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="b431d-103">Felsöka cmdletar</span><span class="sxs-lookup"><span data-stu-id="b431d-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="b431d-104">Så här löser du "varning! Package" ditt paket namn "Det gick inte att ladda ned" problem</span><span class="sxs-lookup"><span data-stu-id="b431d-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="b431d-105">Det rapporteras att `Install-Module` eller `Update-Module` ibland Miss lyckas på vissa datorer.</span><span class="sxs-lookup"><span data-stu-id="b431d-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="b431d-106">Utifrån vår undersökning är det något att göra med nätverks anslutningen.</span><span class="sxs-lookup"><span data-stu-id="b431d-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="b431d-107">Vi har nyligen uppdaterat NuGet-leverantören så att den kan ladda ned paket på ett tillförlitligt sätt.</span><span class="sxs-lookup"><span data-stu-id="b431d-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="b431d-108">Du kan följa anvisningarna nedan om du vill installera den senaste versionen av NuGet-providern och sedan installera eller uppdatera modulen.</span><span class="sxs-lookup"><span data-stu-id="b431d-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="b431d-109">Vi använder Azure-modulen som ett exempel nedan.</span><span class="sxs-lookup"><span data-stu-id="b431d-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="b431d-110">Nätverks slut punkter som krävs</span><span class="sxs-lookup"><span data-stu-id="b431d-110">Required network endpoints</span></span>

<span data-ttu-id="b431d-111">Installations-och uppdaterings-cmdletarna kräver Internet åtkomst för att ansluta till de nätverks slut punkter som används av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b431d-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="b431d-112">Kontrol lera att nätverks åtkomst principerna tillåter att du ansluter till följande slut punkter.</span><span class="sxs-lookup"><span data-stu-id="b431d-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="b431d-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="b431d-113">oneget.org</span></span>
- <span data-ttu-id="b431d-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="b431d-114">go.microsoft.com</span></span>
- <span data-ttu-id="b431d-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="b431d-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="b431d-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="b431d-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="b431d-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="b431d-117">devopsgallerystorage.blob.core.windows.net</span></span>
