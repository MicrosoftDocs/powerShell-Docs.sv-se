---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galleriet, powershell, psgallery BNPR
title: PowerShell-galleriet BNPR kompatibilitet
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189762"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell-galleriet BNPR kompatibilitet

## <a name="overview"></a>Översikt

I kan 2018 träder Europeiska sekretesslagstiftning, den allmänna Data Protection förordning (BNPR), i kraft.
BNPR inför nya regler på företag, myndigheter, icke-vinst och andra organisationer att erbjudande varor och tjänster till personer i Europeiska unionen (EU), eller att samla in och analysera data som är knutna till Europa boende.
BNPR gäller oavsett där du befinner dig.

> [!NOTE]
> Den här artikeln innehåller anvisningar att ta bort personliga data från PowerShell-galleriet och kan användas för att stödja din skyldigheter enligt BNPR. Om du letar efter allmän information om BNPR finns i [BNPR avsnitt av tjänsten förtroende portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Personligt identifierbar information

Följande information som kan utföras av användare som kan innehålla personlig information lagras i PowerShell-galleriet:

* PowerShell-galleriet konto
* Objekt som publicerats i PowerShell-galleriet
* E-postkommunikation med PowerShell-galleriet-teamet

De flesta användare skapar ett konto med PowerShell-galleriet.
Ett konto behövs inte om du ska publicera ett objekt eller funktionen ”kontakta ägare” i PowerShell-galleriet.
Förutom e-postkommunikation initieras av användaren, lagrar inte personligt identifierbar information för användare som inte har skapat ett konto i PowerShell-galleriet.

Användare som skapar ett PowerShell-galleriet konto kan publicera objekt till PowerShell-galleriet.
Dessa objekt förväntas vara PowerShell-koden, men kan innehålla andra information, inklusive personlig information.
Informationen nedan visar hur du kan få alla objekt du har publicerat PowerShell-galleriet.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR Export av Data för PowerShell-galleriet

I följande avsnitt beskrivs hur PowerShell-galleriet stöder ämne begäranden (DSR), som förklarar hur du exporterar information som lagras i PowerShell-galleriet och hur du begär borttagning av den här informationen.

### <a name="email"></a>E-post

E-postkommunikation kan vara något av följande:

* E-post som skickas till ägare av PowerShell-galleriet artiklar om koden analysen skannar upptäckte ett problem med ett objekt som de har publicerats i PowerShell-galleriet
* E-post som skickas av alla till PowerShell-galleriet teamet med hjälp av e-postadress på sidan ”Kontakta oss” (cgadmin@microsoft.com)
* Registrerad användare som använder funktionen ”kontakta ägare” i PowerShell-galleriet för att skicka e-post till ägaren av ett objekt i PowerShell-galleriet

E-postmeddelanden som skickas av eller i PowerShell-galleriet har en bevarandeprincip 90 dagar för att stödja säkerhetsrisker undersökningar bör skadlig kod identifieras på PowerShell-galleriet.
E-postmeddelanden tas bort av Grupprincip efter 90 dagar.

Du kan begära kopior av alla e-postmeddelanden skickas till eller från din e-postadress och PowerShell-galleriet inom de senaste 90 dagarna.
Om du vill begära det här postkommunikation, skicka ett e-postmeddelande till cgadmin@microsoft.com, med rubriken: ”DSR begäran för e-postmeddelanden som är relaterade till det här kontot”.
Ange vilken information som du begär i själva meddelandet (till exempel: skicka alla e-postmeddelanden skickas till eller tas emot från den här e-postadress.) Alla e-post som berör din e-postadress inom 90 dagar efter begäran skickas inom 7 arbetsdagar.

### <a name="powershell-gallery-account-information"></a>PowerShell-galleriet kontoinformation

Om du har skapat ett PowerShell-galleriet konto kan hittar du alla personlig information som har lagrats i PowerShell-galleriet genom att utföra följande steg:

1. Logga in på PowerShell-galleriet och sedan klicka på ditt användarnamn
2. Nästa sida som visas är sidan konto, som visar e-postadressen används för kontot PowerShell-galleriet

Om du har skapat mer än ett konto i PowerShell-galleriet, måste du upprepa dessa steg för varje konto.

### <a name="items-in-the-powershell-gallery"></a>Objekt i PowerShell-galleriet

Vi har publicerat skriptet ”GetPSGalleryItemsForAuthor” i PowerShell-galleriet för att underlätta exporterar objekt som har publicerats i PowerShell-galleriet.
Det här skriptet exporterar en kopia av alla versioner av varje objekt som tas i PowerShell-galleriet baserat på författare informationen som lagras i objektet.

> [!NOTE]
> Författaren lagras i manifestet objektet när du publicerar ditt objekt.
> Det är inte säkert att författaren är samma identitet som det konto som används i PowerShell-galleriet.
> Om du använder ett annat värde i fältet Författare behöver du ange värdet när du använder det här skriptet.

Du kan ladda ned skriptet med hjälp av följande PowerShell-kommando:

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

Sedan kan du köra skriptet direkt, genom att köra följande PowerShell-kommandon:

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

Du uppmanas att ange författaren och en mapp på datorn där du vill att de objekt som ska sparas.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Ta bort personliga Data från PowerShell-galleriet

Ta bort ditt konto med PowerShell-galleriet eller ett objekt som du äger i PowerShell-galleriet genom att skicka e-post till cgadmin@microsoft.com med rubriken: ”BNPR begäran för objekt som är relaterade till det här kontot”.
Ange vilken information som du vill ta bort i själva meddelandet. Till exempel:

* Ta bort version x.y.z för Mina objekt ”namn”
* Ta bort alla versioner av Mina objekt ”namn”
* Ta bort mitt konto PowerShell-galleriet

PowerShell-galleriet administratörer svarar inom 7 arbetsdagar.
De angivna objekt tas bort inom 30 dagar efter att begäran har skickats.
