---
ms.date: 03/27/2018
title: PowerShell-galleriet GDPR-kompatibilitet
description: Den här artikeln förklarar hur du tar bort personliga data från PowerShell-galleriet och kan användas för att stödja dina skyldigheter enligt GDPR.
ms.openlocfilehash: bd2537f48367a9b6ee3a9d70380b1f32d0a1a651
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661140"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell-galleriet GDPR-kompatibilitet

## <a name="overview"></a>Översikt

I maj 2018 trädde en europeisk sekretess lagstiftning, allmän dataskyddsförordning (GDPR). GDPR ålägger nya regler för företag, myndigheter, ideella organisationer och andra organisationer som tillhandahåller varor och tjänster till personer i EU, eller som samlar in och analyserar data som är kopplade till EU-invånare. GDPR gäller oavsett var organisationen har sin verksamhet.

> [!NOTE]
> Den här artikeln innehåller anvisningar för hur du tar bort personliga data från PowerShell-galleriet och kan användas för att stödja dina skyldigheter enligt GDPR. Om du letar efter allmän information om GDPR finns den i [GDPR-avsnittet i Service Trust-portalen](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Personligt identifierbara data

PowerShell-galleriet lagrar följande information som kan tillhandahållas av användare, som kan innehålla personlig information:

- PowerShell-galleriet konto
- Paket som publicerats till PowerShell-galleriet
- E-postkorrespondens med PowerShell-galleriet-teamet

De flesta användare skapar inget PowerShell-galleriet-konto. Det krävs inget konto om du inte ska publicera ett paket eller använda funktionen "kontakta ägare" i PowerShell-galleriet. Förutom e-postkorrespondens som initierats av användaren, lagrar PowerShell-galleriet inte personligt identifierbar information för användare som inte har skapat något konto.

Användare som skapar ett PowerShell-galleriet konto kan publicera paket till PowerShell-galleriet. Dessa paket förväntas vara PowerShell-kod, men kan innehålla annan information, inklusive personlig information. Informationen nedan visar hur du kan hämta alla paket som du har publicerat i PowerShell-galleriet.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR-export av PowerShell-galleriet data

I följande avsnitt beskrivs hur PowerShell-galleriet stöder DSR (data subject requests) genom att förklara hur du exporterar information som lagras i PowerShell-galleriet och hur du begär borttagning av den här informationen.

### <a name="email"></a>E-post

E-postkorrespondens kan vara något av följande:

- E-post som skickas till ägare av PowerShell-galleriet-paket om kod analysen upptäcker ett problem med ett paket som de har publicerat till PowerShell-galleriet
- E-post som skickas av någon till PowerShell-galleriets teamet med hjälp av e-postadressen på sidan kontakta oss [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Registrerade användare som använder funktionen "kontakta ägare" i PowerShell-galleriet för att skicka e-post till ägaren av ett paket i PowerShell-galleriet

E-postmeddelanden som skickas av eller till PowerShell-galleriet har en bevarande princip på 90 dagar för att stödja möjliga säkerhets undersökningar bör skadlig kod identifieras på PowerShell-galleriet. E-postmeddelanden tas bort av en princip efter 90 dagar.

Du kan begära kopior av alla e-postmeddelanden som skickas till eller från din e-postadress och PowerShell-galleriet inom de föregående 90 dagarna. Skicka ett e-postmeddelande till [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com) , med rubriken: "DSR-begäran om e-post som är relaterad till det här kontot", för att begära denna korrespondens. Ange vilken information du begär i meddelandets brödtext (till exempel: skicka alla e-postmeddelanden som skickas till eller tas emot från den här e-postadressen.) Alla e-postmeddelanden som involverar din e-postadress inom 90 dagar från det att begäran skickas inom 7 arbets dagar.

### <a name="powershell-gallery-account-information"></a>PowerShell-galleriet konto information

Om du har skapat ett PowerShell-galleriet konto kan du hitta all personlig information som har lagrats i PowerShell-galleriet genom att utföra följande steg:

1. Logga in på PowerShell-galleriet och klicka sedan på ditt användar namn
2. Nästa sida som visas är konto sidan som visar den e-postadress som används för det PowerShell-galleriet kontot

Om du har skapat fler än ett konto i PowerShell-galleriet måste du upprepa de här stegen för varje konto.

### <a name="packages-in-the-powershell-gallery"></a>Paket i PowerShell-galleriet

För att under lätta exporten av paket som publiceras till PowerShell-galleriet har vi publicerat skriptet "GetPSGalleryItemsForAuthor" till PowerShell-galleriet. Det här skriptet exporterar en kopia av varje version av varje paket som försätts i PowerShell-galleriet baserat på den författar information som lagras i paketet.

> [!NOTE]
> Författaren lagras i paket manifestet när du publicerar ditt paket. Det finns ingen garanti för att författaren är samma identitet som det konto som du använder i PowerShell-galleriet. Om du använder något annat värde i fältet författare måste du ange det värdet när du använder det här skriptet.

Du kan hämta skriptet med hjälp av följande PowerShell-kommando:

```powershell
Save-Script Get-repository psgallery
```

Du kan sedan köra skriptet direkt genom att köra följande PowerShell-kommandon:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Du uppmanas att ange författaren och en mapp i systemet där du vill att paketen ska sparas.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Ta bort personliga data från PowerShell-galleriet

Om du vill ta bort ditt PowerShell-galleriet-konto eller paket som du äger i PowerShell-galleriet skickar du e-post till cgadmin@microsoft.com med rubriken: "GDPR-begäran om objekt som är relaterade till det här kontot". I bröd texten i meddelande läget, vilken information som du vill ta bort. Exempel:

- Ta bort version x. y. z för mitt pakets paket namn.
- Ta bort alla versioner av mitt pakets paket namn.
- Ta bort mitt PowerShell-galleriet-konto

PowerShell-galleriet-administratörer kommer att svara inom 7 arbets dagar.
De angivna paketen tas bort inom 30 dagar efter att begäran har skickats.
