---
ms.date: 06/12/2017
title: Filtrera Sök Resultat
description: I den här artikeln beskrivs användar gränssnittet som används för att filtrera innehåll i PowerShell-galleriet.
ms.openlocfilehash: cc375f3ddb35c95ed134776500bd326bc3db6b1a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661404"
---
# <a name="filtering-search-results"></a>Filtrera Sök Resultat

[Fliken paket](https://www.powershellgallery.com/packages) visar alla tillgängliga paket i PowerShell-galleriet.

Det finns flera sätt att filtrera, sortera och söka i paketen. Klicka på paketet om du vill se mer information om ett visst paket.

## <a name="filter-by"></a>Filtrera efter

Med list rutan filtrera efter kan användare filtrera resultaten genom att:

- Inkludera för hands version
- Endast stabilt

Information om "för hands version" och "stabil" finns i [för hands versions tillägg som läggs till i PowerShellGet och PowerShell-galleriet](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) i PowerShell-teamets blogg.

Med kryss rutorna under List rutan kan användarna filtrera resultaten genom att:

- Paket typer
  - Modul
  - Skript
- Kategorier
  - Cmdlet
  - DSC-resurs
  - Funktion
  - Roll kapacitet
  - Arbetsflöde

Om du bara vill se moduler i PowerShell-galleriet kontrollerar du modulen i paket typerna. På samma sätt kan du kontrol lera skriptet i paket typerna om du bara vill se skript i PowerShell-galleriet.

> [!NOTE]
> Filtren är inkluderade. Exempel: ett paket som innehåller båda cmdletar och funktioner visas om antingen cmdlet eller function (eller båda) är markerade. Om ingen väljs visas inte paketet. På samma sätt visas bara paket som innehåller en av dessa kategorier om du väljer alla kategorier. **Paket som inte tillhör någon av dessa kategorier visas inte.**

## <a name="sort-by"></a>Sortera efter

I list rutan Sortera enligt kan användarna sortera resultaten genom att:

- Popularitet – populariteten bestäms av antalet hämtningar
- A-Z-alfabetiskt efter paket namn
- Senaste-paket visas i ordning av Publicerings datum

## <a name="search-box"></a>Sökruta

Med sökrutan kan användarna söka igenom paketen efter nyckelord.
Mer information finns i [syntax för Galleri sökning](search-syntax.md).
