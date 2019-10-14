---
ms.date: 09/25/2019
keywords: PowerShell, cmdlet
title: Använda PowerShell-dokumentationen
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281645"
---
# <a name="how-to-use-the-powershell-documentation"></a>Använda PowerShell-dokumentationen

Välkommen till PowerShell-onlinedokumentationen. Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:

- PowerShell 7 (för hands version)
- PowerShell 6
- PowerShell 5,1
- PowerShell 5,0
- PowerShell 4,0
- PowerShell 3,0

## <a name="selecting-your-version"></a>Välja din version

Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell. Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell. Se till att du läser dokumentationen för den version av PowerShell som du använder.

Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.

![versions väljare](images/how-to-use-docs/picker-vall.gif)

Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion`-värdet. I följande exempel visas utdata för Windows PowerShell v 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>Söker efter artiklar

Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren. Skriv bara ett ord som visas i rubriken för en artikel. Sidan visar en lista över matchande artiklar. Du kan också välja alternativet att söka igenom hela webbplatsen från listan.

![filter ruta](images/how-to-use-docs/filter-search.gif)
