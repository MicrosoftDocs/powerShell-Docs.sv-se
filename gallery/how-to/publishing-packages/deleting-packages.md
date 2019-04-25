---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Ta bort paket
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084172"
---
# <a name="deleting-packages"></a>Ta bort paket

PowerShell-galleriet har inte stöd för permanent borttagning av paket, eftersom som skulle skapa vem som helst som beroende av den återstående tillgängliga.

I stället PowerShell-galleriet har stöd för ett sätt att ”ta bort” ett paket, det kan du göra på sidan för hantering av paketet på webbplatsen.
När ett paket inte visas, visas den inte längre i sökningar och i alla paket lista, både på PowerShell-galleriet och använder PowerShellGet-kommandon.
Emellertid nedladdningsbara genom att ange den exakta versionen, vilket kan de automatiserade skript för att fortsätta arbeta.

Om du stöter på särskilda omständigheter där du tror att någon av dina paket måste tas bort, kan det hanteras manuellt av PowerShell-galleriet-teamet.
Om det finns en upphovsrättsintrång problemet eller potentiellt skadliga innehåll, som till exempel vara en giltig orsak till att ta bort den.
Du bör skicka en supportbegäran via [PowerShell-galleriet](http://www.PowerShellGallery.com) i så fall.
