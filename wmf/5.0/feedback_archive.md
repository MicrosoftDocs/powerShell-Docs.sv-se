---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057442"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="78b0f-102">Arkiv-cmdletar</span><span class="sxs-lookup"><span data-stu-id="78b0f-102">Archive cmdlets</span></span>

<span data-ttu-id="78b0f-103">Två nya cmdletar **Compress Arkivera** och **Expandera Arkivera**bör du låta du komprimera och expandera ZIP-filer.</span><span class="sxs-lookup"><span data-stu-id="78b0f-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="78b0f-104">Komprimera-Arkiv</span><span class="sxs-lookup"><span data-stu-id="78b0f-104">Compress-Archive</span></span>
<span data-ttu-id="78b0f-105">Den **Compress Arkivera** cmdlet skapar en ny arkivfil från angivna filer.</span><span class="sxs-lookup"><span data-stu-id="78b0f-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="78b0f-106">En fil kan filer med flera paketeras och du kan också komprimerade i en enda fil för enklare hantering och lagring.</span><span class="sxs-lookup"><span data-stu-id="78b0f-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="78b0f-107">En fil som kan komprimeras med hjälp av en komprimeringsalgoritm som anges i den **- CompressionLevel** parametern.</span><span class="sxs-lookup"><span data-stu-id="78b0f-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="78b0f-108">Expandera Arkiv</span><span class="sxs-lookup"><span data-stu-id="78b0f-108">Expand-Archive</span></span>
<span data-ttu-id="78b0f-109">Den **Expandera Arkivera** cmdlet extraherar filer från en angiven arkivfil.</span><span class="sxs-lookup"><span data-stu-id="78b0f-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="78b0f-110">En fil kan filer med flera paketeras och du kan också komprimerade i en enda fil för enklare hantering och lagring.</span><span class="sxs-lookup"><span data-stu-id="78b0f-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
