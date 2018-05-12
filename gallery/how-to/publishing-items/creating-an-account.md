---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapar ett konto med PowerShell-galleriet
ms.openlocfilehash: 3ec9ad8f979fc0b88fbee72fc28ad1e3394eb01d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
## <a name="creating-a-powershell-gallery-account"></a>Skapar ett konto med PowerShell-galleriet

En PowerShell-galleriet måste vara konto innan du publicerar något till PowerShell-galleriet.
PowerShell-galleriet konton måste kopplas till ett e-postaktiverade Azure Active Directory-konto eller ett Microsoft-konto för e-post (med en domän till outlook.com, hotmail.com osv.)

Om du vill skapa ett PowerShell-galleriet-konto går du till https://PowerShellGallery.com och klicka på ”registrera” (se bilden nedan).

![Registrera nytt konto](../../Images/CreatingAccount-Register.png)

Välj ”arbets eller Skolkonto” om du vill använda ett Azure Active Directory-konto och logga in med ditt konto på nästa sida.
Välj ”personliga konto” om du vill använda ett Microsoft-konto – till exempel en i en Hotmail.com eller Outlook.com domän - och logga in.

När du har loggat in uppmanas du att skapa ett användarnamn för PowerShell-galleriet.
Granska användningsvillkoren och sekretesspolicyn för som är länkade i, ange ett användarnamn och klicka sedan på registrera.

Obs: Den här kontonamn kan inte ändras när den har skapats.
Se [hantera objekt ägare](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) för ytterligare information om det här.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Rekommenderade metoder för PowerShell-galleriet konton

Det är viktigt att e-postkontot som används med PowerShell-galleriet kontot övervakas aktivt.
Alla communiction med ägare av PowerShell galleriobjekt är via e-postmeddelandet med den adress som är kopplad till ditt konto med PowerShell-galleriet.
Om vi inte går att kontakta en artikel ägare, kan driftteamet behöva ta bort ett objekt i vissa fall.

Organisationer som publicerar i PowerShell-galleriet ofta skapa ett unikt konto för detta ändamål i Outlook.com eller domänen med ett annat Microsoft-konto.
I många fall övervakas det kontot regelbundet inte.
Bästa praxis är i så fall att använda Outlook vidarebefordran för att skicka e-post till ett annat konto, vanligtvis en inom organisationen som ska övervakas av objektet ägare.

Om det finns flera ägare som är associerad med ett objekt, kommer all kommunikation som kommer från PowerShell-galleriet gå till alla ägare.
Se [hantera objekt ägare](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) för mer information om hur du lägger till ägare till ett objekt.