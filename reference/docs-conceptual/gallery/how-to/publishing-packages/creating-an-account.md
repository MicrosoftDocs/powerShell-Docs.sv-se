---
ms.date: 09/11/2018
title: Skapa ett PowerShell-galleriet konto
description: Den här artikeln beskriver användar konto kraven för PowerShell-galleriet
ms.openlocfilehash: 24c7531e61128415a284d1b438b43f3af0d1053a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662615"
---
# <a name="creating-a-powershell-gallery-account"></a>Skapa ett PowerShell-galleriet konto

Du måste skapa ett PowerShell-galleriet konto innan du publicerar något till PowerShell-galleriet.
PowerShell-galleriet konton måste vara länkade till ett e-postaktiverat inloggnings konto. Det här kontot kan vara ett Azure Active Directory konto eller ett Microsoft-ID, t. ex. ett e-postkonto från outlook.com eller hotmail.com.

Om du vill skapa ett PowerShell-galleriet konto går du till [https://PowerShellGallery.com](https://PowerShellGallery.com) och klickar på **Logga** in som visas i följande bild.

![Registrera nytt konto](media/creating-an-account/CreateAccount-Register.png)

Om du vill använda ett Azure Active Directory konto väljer du **arbets-eller skol konto** och loggar in med ditt konto. Om du vill använda ett Microsoft-ID väljer du **personligt konto** och loggar in.

Därefter uppmanas du att skapa ett användar namn för PowerShell-galleriet. Granska användnings villkoren och sekretess policyn, ange ett användar namn och klicka sedan på **Registrera** .

> [!NOTE]
> Det går inte att ändra konto namnet när det har skapats. Mer information finns i [Hantera paket ägare](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Rekommenderade metoder för PowerShell-galleriet konton

Det är viktigt att aktivt övervaka det e-postkonto som används med ditt PowerShell-galleriet-konto. All kommunikation med ägare av PowerShell-galleriet-paket är via den här e-postadressen. Om PowerShell-galleriet Operations-teamet inte kan kontakta en paket ägare kan vi behöva ta bort ett paket.

Organisationer som publicerar till PowerShell-galleriet ofta skapar ett unikt externt konto för detta ändamål. Vi rekommenderar att du använder e-postvidarebefordran för att vidarebefordra meddelanden till en adress i din organisation.

När flera ägare är associerade med ett paket skickas alla PowerShell-galleriet meddelanden till alla ägare. Mer information finns i [Hantera paket ägare](managing-package-owners.md).
