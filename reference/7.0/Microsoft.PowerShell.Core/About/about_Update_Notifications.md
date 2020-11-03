---
description: Meddelar användare om start av PowerShell att en ny version av PowerShell har släppts.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: ea6b768ef62679ee039b156b72e69a7ba240389f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271329"
---
# <a name="about-update-notifications"></a>Om uppdaterings meddelanden

## <a name="short-description"></a>KORT BESKRIVNING

Meddelar användare om start av PowerShell att en ny version av PowerShell har släppts.

## <a name="long-description"></a>LÅNG BESKRIVNING

Från och med PowerShell 7,0 använder PowerShell uppdaterings meddelanden för att varna användarna om att det finns uppdateringar till PowerShell. En gång per dag frågar PowerShell en online tjänst för att avgöra om det finns en nyare version.

> [!NOTE]
> Även om uppdaterings kontrollen sker under den första sessionen under en viss 24-timmarsperiod, kan du av prestanda skäl bara se meddelandet i början av efterföljande sessioner. Av prestanda skäl kommer kontrollen inte att starta förrän minst tre sekunder efter att sessionen har påbörjats.

Som standard prenumererar PowerShell på en av två olika meddelande kanaler, beroende på dess version/gren. Allmänt tillgängliga (GA) versioner av PowerShell returnerar endast aviseringar för uppdaterade GA-versioner. För hands versions-och Release Candidate (RC)-versioner meddelar uppdateringar om uppdateringar för Preview-, RC-och GA-versioner.

Du kan ändra beteendet för uppdaterings aviseringar med hjälp av `POWERSHELL_UPDATECHECK` miljövariabeln. Följande värden stöds:

- `Off` inaktiverar funktionen för uppdaterings avisering
- `Default` är detsamma som att inte definiera `POWERSHELL_UPDATECHECK` :
  - GA-versioner meddelar uppdateringar till GA-versioner
  - Preview/RC-versioner meddelar uppdateringar för GA och för hands versioner
- `LTS` endast meddelanden om uppdateringar av LTS (långsiktig service) GA-versioner

Följande slut punkter används för närvarande för att fastställa den senaste versionen av varje kanal:

- `LTS`: https://aka.ms/pwsh-buildinfo-lts
- `Stable`: https://aka.ms/pwsh-buildinfo-stable
- `Preview`: https://aka.ms/pwsh-buildinfo-preview

Uppdaterings meddelandet ger inte något sätt att automatiskt uppdatera PowerShell. I framtiden kan det finnas fler instruktioner eller funktioner att uppdatera från PowerShell, men idag bör du använda samma installations metod som du använde för att installera PowerShell för att uppdatera den.
