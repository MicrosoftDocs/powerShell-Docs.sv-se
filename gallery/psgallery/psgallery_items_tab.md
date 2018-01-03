---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a>Fliken objekt

Den [fliken poster](https://www.powershellgallery.com/items) visar alla tillgängliga objekt i PowerShell-galleriet.

Det finns flera sätt att filtrera, sortera och söka efter objekt.
Om du vill ha mer information om ett visst objekt, klickar du på objektet.

## <a name="filter-by"></a>Filtrera efter

I listrutan under ”filtrera efter” tillåter användare att filtrera resultaten genom att:
* Inkludera förhandsversion
* Stabil endast

Information om ”förhandsversion” och ”stabil” finns [förhandsversion versionshantering lagts till PowerShellGet och PowerShell-galleriet](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) i PowerShell-teamets blogg.

Kryssrutorna under listrutan Tillåt användare att filtrera resultaten genom att:
* Typer av objekt
  - Modul
  - Skript
* Kategorier
  - Cmdlet
  - DSC-resurs
  - Funktion
  - Kapaciteten för rollen
  - Arbetsflöde

Kontrollera modul i vilka typer av objekt om du vill visa endast moduler i PowerShell-galleriet.
På samma sätt för att se endast skript i PowerShell-galleriet, kontrollera skriptet i vilka typer av objekt.

> [!NOTE]
> Filter är inklusiva.
> Exempel: Ett objekt som innehåller både cmdletar och funktioner visas om antingen Cmdlet eller funktionen (eller båda) är markerade.
> Om ingen väljs visas inte objektet.
> Om alla kategorier har valts visas och endast objekt som innehåller en av dessa kategorier.
> **Objekt som inte tillhör någon av dessa kategorier visas inte.**

## <a name="sort-by"></a>Sortera efter

Sortera efter listrutan tillåter användare att sortera resultaten efter:
* Popularitet - popularitet bestäms genom att hämta antalet
* A-Z - alfabetiskt efter namn
* Senaste - objekt som visas i den ordning de publicera datum

## <a name="search-box"></a>Sökrutan

Sökrutan tillåter användare att söka efter objekt på nyckelord.
Mer information finns i [galleriet Söksyntax](psgallery_search_syntax.md).
