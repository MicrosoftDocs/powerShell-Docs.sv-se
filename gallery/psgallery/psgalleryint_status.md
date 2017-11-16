---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a>PowerShell-galleriet Status
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017-03/27 - löst: Det gick inte att visa enskilda sidor för modulen och skript

__Sammanfattning av påverkan__: Dirigera länkar till modulen och skript på enskilda sidor https://www.powershellgallery.com bröts. Detta har rapporterats i alla regioner. Det inte att påverka PowerShellGet cmdlets ie., installera modulen installationsskriptet, Update-Module-skript för att uppdatera, publicera-modulen, publicera-skript fortsätter att fungera.

__Rotorsak__: Engineers identifieras orsaken som ett problem med att samla in sociala medier knappar som Facebook till sidan.  

__Lösning__: Engineers problemet genom att inaktivera Facebook antalsinformation.

__Nästa steg__: vi öppnas ett internt spårning problem för att åtgärda vår användning av Facebook-API.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>2016/12/15 - det går inte att skicka e-post via PowerShellGallery webbplats

__Sammanfattning av påverkan__: mellan 2016/12/13 och 2016/12/15 alla meddelanden som skickas via kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk har inte tagits emot av PowerShell-galleriet administratörer.  
__Rotorsak__: Engineers identifieras orsaken som autentiseringsproblem med SMTP-servern.  
__Lösning__: Engineers kunde lösa problemet för autentisering och återställa anslutningen till SMTP-servern.  
__Nästa steg__: Om du använde kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk länkar för att skicka e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen. Vi ber om ursäkt för besväret.   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>8/10/2016 - löst: Det gick inte att skicka e-postmeddelandencgadmin@microsoft.com
__Sammanfattning av påverkan__: mellan 2016-8-5 och 2016-8-10 kunder kunde inte skicka e-postmeddelanden cgadmin@microsoft.com, eller använda funktionen Kontakta oss.  
__Rotorsak__: Engineers identifieras orsaken som en konfigurationsändring av e-postkonto.  
__Lösning__: Engineers arbetat för att lösa problemet konfiguration.  
__Nästa steg__: Om du har använt länken Kontakta oss eller skickas e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen. Tack för ditt tålamod.


