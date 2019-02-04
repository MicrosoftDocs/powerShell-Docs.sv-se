---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Filtrera sökresultaten
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687596"
---
# <a name="filtering-search-results"></a>Filtrera sökresultaten

Den [paket fliken](https://www.powershellgallery.com/packages) visar alla tillgängliga paket i PowerShell-galleriet.

Det finns flera sätt att filtrera, sortera och söka paketen.
Om du vill se mer information om ett visst paket, klickar du på paketet.

## <a name="filter-by"></a>Filtrera efter

I listrutan under ”filtrera efter” tillåter användare att filtrera resultatet efter:
- Inkludera förhandsversion
- Stabil endast

Läs om hur ”förhandsversion” och ”stabil” [förhandsversion versionshantering som har lagts till i PowerShellGet och PowerShell-galleriet](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) i PowerShell-teamets blogg.

Kryssrutorna under listrutan kan du filtrera resultatet efter:
- Pakettyper
  - Modul
  - Skript
- Kategorier
  - Cmdlet
  - DSC-resurs
  - Funktion
  - Kapaciteten för rollen
  - Arbetsflöde

Kontrollera modul i den pakettyper endast moduler i PowerShell-galleriet visas.
På samma sätt för att visa endast skript i PowerShell-galleriet, kontrollera skriptet i den pakettyper.

> [!NOTE]
> Filter är inkluderande.
> Exempel: Ett paket som innehåller både cmdletar och funktioner visas om antingen Cmdlet eller funktion (eller båda) är markerade.
> Om ingen av dem har valts, visas inte paketet.
> Om alla kategorier har valts visas på samma sätt kan endast paket som innehåller en av dessa kategorier.
> **Paket som inte tillhör någon av dessa kategorier visas inte.**

## <a name="sort-by"></a>Sortera efter

Sortera efter listrutan kan du sortera resultaten efter:
- Popularitet - popularitet bestäms genom att hämta antal
- A-Z - alfabetiskt efter paketnamn
- Senaste - paket som visas i ordningen för publiceringsdatum

## <a name="search-box"></a>Sökrutan

Sökrutan tillåter användare att söka i paketen på nyckelord.
Mer information finns i [Gallerisökning](search-syntax.md).
