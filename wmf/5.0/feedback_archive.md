---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218101"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="60892-102">Arkiv-cmdlets</span><span class="sxs-lookup"><span data-stu-id="60892-102">Archive cmdlets</span></span>

<span data-ttu-id="60892-103">Två nya cmdlet: ar, **komprimera Arkiv** och **Expandera arkivet**, kan du komprimera och expandera ZIP-filer.</span><span class="sxs-lookup"><span data-stu-id="60892-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="60892-104">Komprimera-Arkiv</span><span class="sxs-lookup"><span data-stu-id="60892-104">Compress-Archive</span></span>
<span data-ttu-id="60892-105">Den **komprimera Arkiv** cmdlet skapar en ny arkivfil från angivna filer.</span><span class="sxs-lookup"><span data-stu-id="60892-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="60892-106">En fil kan flera filer till paketeras och eventuellt komprimerade till en enda fil för enklare hantering och lagring.</span><span class="sxs-lookup"><span data-stu-id="60892-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="60892-107">En fil som kan komprimeras med hjälp av en komprimeringsalgoritm som anges i den **- CompressionLevel** parameter.</span><span class="sxs-lookup"><span data-stu-id="60892-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="60892-108">Expandera arkivet</span><span class="sxs-lookup"><span data-stu-id="60892-108">Expand-Archive</span></span>
<span data-ttu-id="60892-109">Den **Expandera arkivet** cmdlet extraherar filer från en angiven arkivfilen.</span><span class="sxs-lookup"><span data-stu-id="60892-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="60892-110">En fil kan flera filer till paketeras och eventuellt komprimerade till en enda fil för enklare hantering och lagring.</span><span class="sxs-lookup"><span data-stu-id="60892-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
