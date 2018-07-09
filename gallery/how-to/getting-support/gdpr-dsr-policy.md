---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galleriet, powershell, psgallery, GDPR
title: PowerShell-galleriet GDPR-kompatibilitet
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893254"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell-galleriet GDPR-kompatibilitet

## <a name="overview"></a>Översikt

En europeisk lag är den allmänna Dataskyddsförordningen GDPR (Data Protection), börjar gälla i maj 2018.
Dataskyddsförordningen inför nya regler på företag, myndigheter, ideella och andra organisationer att erbjudandet varor och tjänster till personer i Europeiska unionen (EU) eller att samla in och analysera data som EU invånare.
Dataskyddsförordningen gäller oavsett var du befinner dig.

> [!NOTE]
> Den här artikeln innehåller anvisningar att ta bort personliga data från PowerShell-galleriet och kan användas för att stödja dina skyldigheter enligt GDPR. Om du letar efter allmän information om GDPR finns i den [GDPR-delen av den Service Trust portalen](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Personligt identifierbar information

PowerShell-galleriet lagrar följande information som tillhandahålls av användare, som kan innehålla personlig information:

- PowerShell-galleriet konto
- Objekt som publicerats i PowerShell-galleriet
- E-postkommunikation med PowerShell-galleriet-teamet

De flesta användare skapa inte ett konto med PowerShell-galleriet.
Ett konto krävs inte om du ska publicera ett objekt eller funktionen ”kontakta ägare” i PowerShell-galleriet.
Förutom e-postkommunikation initieras av användaren, lagrar inte PowerShell-galleriet personligt identifierbar information för användare som inte har skapat ett konto.

Användare som skapar ett konto med PowerShell-galleriet kan publicera objekt PowerShell-galleriet.
Dessa objekt förväntas vara PowerShell-kod, men kan innehålla andra information inklusive personlig information.
Informationen nedan visar hur du kan få alla objekt du har publicerat PowerShell-galleriet.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR-Export av Data för PowerShell-galleriet

I följande avsnitt beskrivs hur PowerShell-galleriet stöder DSR-begäranden (DSR) genom att förklara hur du exporterar information som lagras i PowerShell-galleriet och hur du begär borttagning av den här informationen.

### <a name="email"></a>E-post

E-postkommunikation kan vara något av följande:

- E-postmeddelande skickas till innehavare av PowerShell-galleriet objekt om kod analysen söker igenom har upptäckt ett problem med ett objekt som de har publicerats i PowerShell-galleriet
- E-post som skickas av vem som helst till PowerShell-galleriet teamet med den e-postadressen på sidan ”Kontakta oss” [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Registrerad användare som använder funktionen ”kontakta ägare” i PowerShell-galleriet för att skicka e-postmeddelande till ägaren av ett objekt i PowerShell-galleriet

E-postmeddelanden som skickas av eller PowerShell-galleriet har en bevarandeprincip 90 dagar för att stödja säkerhetsrisker undersökningar bör skadlig kod identifieras på PowerShell-galleriet.
E-postmeddelanden tas bort av Grupprincip efter 90 dagar.

Du kan begära kopior av alla e-postmeddelanden skickas till eller från din e-postadress och PowerShell-galleriet inom de senaste 90 dagarna.
Om du vill begära det här postkommunikation, skicka ett e- [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), med rubriken: ”DSR-begäran för e-postmeddelanden som är relaterade till det här kontot”.
Ange vilken information som du begär i meddelandets brödtext (till exempel: skicka alla e-postmeddelanden skickas till eller tas emot från den här e-postadress.) Alla e-postmeddelanden som rör din e-postadress inom 90 dagar från förfrågan skickas inom 7 affärsdagar.

### <a name="powershell-gallery-account-information"></a>Information om PowerShell-galleriet

Om du har skapat ett konto med PowerShell-galleriet hittar du all personlig information som har lagrats i PowerShell-galleriet genom att utföra följande steg:

1. Logga in på PowerShell-galleriet och sedan klicka på ditt användarnamn
2. Nästa sida som visas är sidan som visar e-postadressen används för PowerShell-galleriet

Om du har skapat fler än ett konto i PowerShell-galleriet, måste du upprepa dessa steg för varje konto.

### <a name="items-in-the-powershell-gallery"></a>Objekt i PowerShell-galleriet

För att underlätta exporterar objekt som publicerats i PowerShell-galleriet, har vi publicerat skriptet ”GetPSGalleryItemsForAuthor” PowerShell-galleriet.
Det här skriptet exporterar en kopia av alla versioner av varje objekt i PowerShell-galleriet baserat på författare informationen som lagras i objektet.

> [!NOTE]
> Författaren lagras i manifestet objekt när du publicerar dina objekt.
> Det finns ingen garanti att författaren är samma identitet som det konto som används i PowerShell-galleriet.
> Om du använder ett annat värde i fältet Författare, måste du ange detta värde när du använder det här skriptet.

Du kan ladda ned skriptet med hjälp av följande PowerShell-kommando:

```powershell
Save-Script Get-repository psgallery
```

Du kan sedan köra skriptet direkt, genom att köra följande PowerShell-kommandon:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Du uppmanas att ange författaren och en mapp på datorn där du vill att de objekt som ska sparas.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Ta bort personliga Data från PowerShell-galleriet

Om du vill ta bort ditt konto med PowerShell-galleriet eller vilket objekt som du äger i PowerShell-galleriet, skicka e-postmeddelande till cgadmin@microsoft.com med rubriken: ”GDPR-begäran för artiklar som är relaterade till det här kontot”.
Ange vilken information som du vill ta bort i brödtexten i meddelandet. Till exempel:

- Ta bort version x.y.z för Mina objekt ”objektnamn”
- Ta bort alla versioner av Mina objekt ”objektnamn”
- Ta bort mitt konto för PowerShell-galleriet

PowerShell-galleriet administratörer kommer att svara inom 7 affärsdagar.
De angivna objekt tas bort inom 30 dagar efter att begäran har skickats.