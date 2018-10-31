---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapa ett konto med PowerShell-galleriet
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004165"
---
# <a name="creating-a-powershell-gallery-account"></a>Skapa ett konto med PowerShell-galleriet

Du måste skapa ett PowerShell-galleriet-konto innan du publicerar något i PowerShell-galleriet.
PowerShell-galleriet konton måste kopplas till en e-postaktiverade inloggningskonto. Det här kontot kan vara ett Azure Active Directory-konto eller ett Microsoft-ID, t.ex. ett e-postkonto från outlook.com eller hotmail.com.

Om du vill skapa ett PowerShell-galleriet-konto går du till [ https://PowerShellGallery.com ](https://PowerShellGallery.com) och klicka på **logga in** enligt följande bild.

![Registrera nytt konto](../../Images/CreateAccount-Register.png)

Om du vill använda ett Azure Active Directory-konto, Välj **arbets- eller Skolkonto**, och logga in med ditt konto. Om du vill använda ett Microsoft-ID, Välj **personligt konto** och logga in.

Därefter uppmanas du att skapa ett användarnamn för PowerShell-galleriet. Granska användningsvillkor och sekretesspolicy, ange ett användarnamn och klicka sedan på **registrera**.

> [!NOTE]
> Namnet på kontot kan inte ändras när den har skapats. Mer information finns i [hantera paket ägare](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Rekommenderade metoder för konton med PowerShell-galleriet

Det är viktigt att övervaka aktivt e-postkontot som används med ditt konto med PowerShell-galleriet. All kommunikation med ägare av PowerShell-galleriet paket är via e-postadressen. Om PowerShell-galleriet driftsteamet kan inte kontakta en paketets ägare, kan vi behöva ta bort ett paket.

Organisationer som publicerar till PowerShell-galleriet ofta skapa en unik externt konto för detta ändamål. Vi rekommenderar att du använder vidarebefordra e-post för att vidarebefordra meddelanden till en adress inom din organisation.

När flera ägare är associerad med ett paket, skickas meddelanden för alla PowerShell-galleriet för alla användare. Mer information finns i [hantera paket ägare](managing-package-owners.md).
