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
# <a name="archive-cmdlets"></a>Arkiv-cmdletar

Två nya cmdletar **Compress Arkivera** och **Expandera Arkivera**bör du låta du komprimera och expandera ZIP-filer.

## <a name="compress-archive"></a>Komprimera-Arkiv
Den **Compress Arkivera** cmdlet skapar en ny arkivfil från angivna filer. En fil kan filer med flera paketeras och du kan också komprimerade i en enda fil för enklare hantering och lagring. En fil som kan komprimeras med hjälp av en komprimeringsalgoritm som anges i den **- CompressionLevel** parametern.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expandera Arkiv
Den **Expandera Arkivera** cmdlet extraherar filer från en angiven arkivfil. En fil kan filer med flera paketeras och du kan också komprimerade i en enda fil för enklare hantering och lagring.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
