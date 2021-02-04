---
ms.date: 07/29/2020
keywords: powershell,cmdlet
ms.topic: how-to
title: Använda PowerShell-dokumentationen
description: I den här artikeln beskrivs hur du använder funktionerna i den här webbplatsen, inklusive Sök filtrering och versions val.
ms.openlocfilehash: 4779e6e4b17c461d71e9d613d1184b9ce2e7ab7b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216090"
---
# <a name="how-to-use-the-powershell-documentation"></a>Använda PowerShell-dokumentationen

Välkommen till PowerShell-onlinedokumentationen. Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:

- PowerShell 7,2 (för hands version)
- PowerShell 7,1 (aktuell)
- PowerShell 7,0 (LTS)
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Hitta artiklar och välja en version

Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren. Skriv bara ett ord som visas i rubriken för en artikel. Sidan visar en lista över matchande artiklar. Du kan också välja alternativet att söka igenom hela webbplatsen från listan.

Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell. Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell. Se till att du läser dokumentationen för den version av PowerShell som du använder.

Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.

![Använda versions väljaren](media/how-to-use-docs/version-search.gif)

Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion` värdet. I följande exempel visas utdata för Windows PowerShell 5,1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

Om du inte har använt PowerShell igen och behöver hjälp med att förstå kommandosyntaxen, se [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).

## <a name="finding-articles-for-previous-versions"></a>Hitta artiklar för tidigare versioner

Dokumentationen för äldre versioner av PowerShell har arkiverats på vår [tidigare versions](https://aka.ms/PSLegacyDocs) webbplats.

Den här platsen innehåller dokumentation för följande ämnen:

- PowerShell 3.0
- PowerShell 4.0
- PowerShell 5.0
- PowerShell 6
- PowerShell-arbetsflöden
- PowerShell-Webbåtkomst
