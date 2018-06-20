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
# <a name="archive-cmdlets"></a>Arkiv-cmdlets

Två nya cmdlet: ar, **komprimera Arkiv** och **Expandera arkivet**, kan du komprimera och expandera ZIP-filer.

## <a name="compress-archive"></a>Komprimera-Arkiv
Den **komprimera Arkiv** cmdlet skapar en ny arkivfil från angivna filer. En fil kan flera filer till paketeras och eventuellt komprimerade till en enda fil för enklare hantering och lagring. En fil som kan komprimeras med hjälp av en komprimeringsalgoritm som anges i den **- CompressionLevel** parameter.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expandera arkivet
Den **Expandera arkivet** cmdlet extraherar filer från en angiven arkivfilen. En fil kan flera filer till paketeras och eventuellt komprimerade till en enda fil för enklare hantering och lagring.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
