---
ms.date: 06/12/2017
title: Ta bort paket från PowerShell-galleriet
description: Ta bort paket från PowerShell-galleriet
ms.openlocfilehash: e02fad61ce8ab808ba9fdf4ab16b9ae236a49e80
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662570"
---
# <a name="deleting-packages"></a>Ta bort paket

PowerShell-galleriet har inte stöd för permanent borttagning av paket, eftersom det skulle bryta alla som är beroende av den återstående tillgänglig.

I stället har PowerShell-galleriet stöd för ett-paket, som kan göras på sidan paket hantering på webbplatsen. När ett paket inte visas i listan visas det inte längre i Sök och i någon paket lista, både på PowerShell-galleriet och med PowerShellGet-kommandon.
Men det är fortfarande nedladdnings Bart genom att ange dess exakta version, vilket är det som tillåter att de automatiserade skripten fortsätter att fungera.

Om du stöter på en situation där du tror att ett av dina paket måste tas bort, kan det hanteras manuellt av PowerShell-galleriets teamet. Om det till exempel finns ett problem med upphovs rätts intrång eller potentiellt skadligt innehåll, kan det vara en giltig anledning att ta bort den. Du bör skicka in en support förfrågan via [PowerShell-galleriet](https://www.PowerShellGallery.com) i detta fall.
