---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
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

