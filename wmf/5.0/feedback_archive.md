---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
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