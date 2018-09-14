---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapa ett konto med PowerShell-galleriet
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522851"
---
# <a name="creating-a-powershell-gallery-account"></a>Skapa ett konto med PowerShell-galleriet

Du måste skapa ett PowerShell-galleriet-konto innan du publicerar något i PowerShell-galleriet.
PowerShell-galleriet konton måste kopplas till en e-postaktiverade inloggningskonto. Det här kontot kan vara ett Azure Active Directory-konto eller ett Microsoft-ID, t.ex. ett e-postkonto från outlook.com eller hotmail.com.

Om du vill skapa ett PowerShell-galleriet-konto går du till [ https://PowerShellGallery.com ](https://PowerShellGallery.com) och klicka på **logga in** enligt följande bild.

![Registrera nytt konto](../../Images/CreateAccount-Register.png)

Om du vill använda ett Azure Active Directory-konto, Välj **arbets- eller Skolkonto**, och logga in med ditt konto. Om du vill använda ett Microsoft-ID, Välj **personligt konto** och logga in.

Därefter uppmanas du att skapa ett användarnamn för PowerShell-galleriet. Granska användningsvillkor och sekretesspolicy, ange ett användarnamn och klicka sedan på **registrera**.

> [!NOTE]
> Namnet på kontot kan inte ändras när den har skapats. Mer information finns i [hantera objektägare](managing-item-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Rekommenderade metoder för konton med PowerShell-galleriet

Det är viktigt att övervaka aktivt e-postkontot som används med ditt konto med PowerShell-galleriet. All kommunikation med ägare av objekt PowerShell-galleriet är via e-postadressen. Om PowerShell-galleriet driftsteamet kan inte kontakta ägare objekt, kan vi behöva ta bort ett objekt.

Organisationer som publicerar till PowerShell-galleriet ofta skapa en unik externt konto för detta ändamål. Vi rekommenderar att du använder vidarebefordra e-post för att vidarebefordra meddelanden till en adress inom din organisation.

När flera ägare är associerad med ett objekt, skickas meddelanden för alla PowerShell-galleriet för alla användare. Mer information finns i [hantera objektägare](managing-item-owners.md).
