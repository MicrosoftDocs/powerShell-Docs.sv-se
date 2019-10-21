---
ms.date: 10/20/2019
keywords: PowerShell, cmdlet
title: Använda PowerShell-dokumentationen
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: ac1ccdd826f112a11db09af9c628cae013f947ab
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/20/2019
ms.locfileid: "72676177"
---
# <a name="how-to-use-the-powershell-documentation"></a>Använda PowerShell-dokumentationen

Välkommen till PowerShell-onlinedokumentationen. Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:

- PowerShell 7 (för hands version)
- PowerShell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Hitta artiklar och välja en version

Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren. Skriv bara ett ord som visas i rubriken för en artikel. Sidan visar en lista över matchande artiklar. Du kan också välja alternativet att söka igenom hela webbplatsen från listan.

Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell. Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell. Se till att du läser dokumentationen för den version av PowerShell som du använder.

Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.

![versions väljare](images/how-to-use-docs/version-search.gif)

Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion`-värdet. I följande exempel visas utdata för Windows PowerShell v 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
