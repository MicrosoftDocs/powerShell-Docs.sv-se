---
title: Bidra till PowerShell-dokumentation
description: Den här artikeln är en översikt över hur du kommer igång som en deltagare i PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 5db78ae2805cb26aa79aa698cfb8b5d8ba8911dc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "79407051"
---
# <a name="contributing-to-powershell-documentation"></a>Bidra till PowerShell-dokumentation

Tack för ditt stöd för PowerShell!

Bidrags guidens guide är en samling artiklar som förklarar de verktyg och processer som vi använder för att skapa dokumentation på Microsoft. Några av de här vägledningarna beskriver information som är gemensam för alla dokumentations uppsättningar som publicerats på [docs.Microsoft.com][docs]. Några av guiderna är speciella för hur vi skriver dokumentation för PowerShell.

De vanliga artiklarna är tillgängliga i vårt centraliserade [bidrags guide][contribute]. PowerShell-/regionsspecifika guider finns här.

## <a name="ways-to-contribute"></a>Sätt att bidra

Det finns två sätt att bidra. Båda bidragen är värdefulla för oss.

- Genom att [arkivera problem][file-an-issue] kan vi identifiera problem och luckor i vår dokumentation. Ibland är problemen svåra att lösa, vilket kräver mer undersökningar och forskning. Med ärende processen kan vi få en konversation om problemet och utveckla en tillfredsställande lösning.

- Att skicka nytt innehåll eller ändringar i befintliga artiklar är en mer engagerad process. Följande information beskriver verktyg, processer och standarder för att skicka innehåll till dokumentationen.

## <a name="prepare-to-make-a-contribution"></a>Förbered för att göra ett bidrag

Du behöver ett GitHub-konto för att bidra till dokumentationen. Använd följande check lista för att hämta verktyg och förstå de processer som vi använder för att göra bidrag.

1. [Registrera dig för GitHub](/contribute/get-started-setup-github)
1. [Installera Git- och Markdown-verktyg](/contribute/get-started-setup-tools)
1. [Installera redigerings paketet för dokument](/contribute/how-to-write-docs-auth-pack)
1. [Installera posh-git][posh-git] – inte obligatoriskt, men rekommenderas
1. [Konfigurera en lokal Git-lagringsplats](/contribute/get-started-setup-local)
1. [Granska git och GitHub fundament ALS](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a>Komma igång med att skriva dokument

Det finns två sätt att bidra till ändringar i dokumentationen:

1. [Snabb redigering av befintliga dokument](/contribute/#quick-edits-to-existing-documents)
   - Mindre korrigeringar, korrigering av skrivfel eller små tillägg
1. [Fullständigt GitHub-arbetsflöde för dokument](/contribute/how-to-write-workflows-major)
   - stora ändringar, flera versioner, lägga till eller ändra bilder eller bidra med nya artiklar

Läs även avsnittet [Skriv Essentials](/contribute/style-quick-start) i den centrala deltagarens guide. En annan utmärkt resurs är [Microsofts Skriv stils guide][style-guide]. Målet med Microsoft writing Style Guide är att hjälpa redigerare, tekniska skrivare, utvecklare, marknads förare och andra i IT att skriva bättre innehåll.

Mindre korrigeringar eller klargöranden av dokumentation och kod exempel i offentliga databaser omfattas av docs.microsoft.com användnings [villkor][terms-of-use].

Använd det fullständiga GitHub-arbetsflödet när du gör betydande ändringar. Om du inte är anställd hos Microsoft genererar betydande ändringar en kommentar i pull-begäran som ber dig att skicka ett [licens avtal för CLA (online bidrag)][cla]. Du måste fylla i hela online-formuläret innan vi kan granska eller acceptera din pull-begäran.

## <a name="code-of-conduct"></a>Uppförandekod

Alla informationslager som publicerar till docs.microsoft.com har antagit [Microsoft Open Source-uppförandekoden](https://opensource.microsoft.com/codeofconduct/) eller [.NET Foundation-uppförandekoden](https://dotnetfoundation.org/code-of-conduct). Mer information finns i [Vanliga frågor och svar om uppförandekod](https://opensource.microsoft.com/codeofconduct/faq/).

## <a name="next-steps"></a>Nästa steg

Följande artiklar beskriver information som är unik för PowerShell-dokumentationen. Om det finns överlappande vägledning i den centraliserade deltagar guiden, så kallar vi hur reglerna skiljer sig åt för PowerShell-innehållet.

Läs följande dokument:

- [Så här arkiverar du ett problem](file-an-issue.md)
- [Komma igång med att skriva dokument](get-started-writing.md)
- [Skicka en pull-begäran](pull-requests.md)
- [Stilguide för PowerShell-Docs](powershell-style-guide.md)
- [Redigera cmdlet-referens](editing-cmdlet-ref.md)

Ytterligare resurser

- [Checklista för redigering](editorial-checklist.md)
- [Så här hanterar vi problem](managing-issues.md)
- [Så här hanterar vi pull-begäranden](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: https://docs.microsoft.com/powershell
[style-guide]: https://docs.microsoft.com/style-guide/welcome/
[terms-of-use]: https://docs.microsoft.com/legal/termsofuse