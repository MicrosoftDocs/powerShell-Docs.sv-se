---
title: Skicka pull-begäranden
description: Den här artikeln beskriver hur du skickar pull-begäranden till PowerShell-Docs-lagringsplatsen.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090217"
---
# <a name="how-to-submit-pull-requests"></a>Skicka pull-begäranden

Skicka en pull-begäran (PR) från din förgrening om du vill göra ändringar i innehållet. En pull-begäran måste granskas innan den kan slås samman. För bästa resultat bör du läsa igenom [redaktionell check lista](editorial-checklist.md) innan du skickar din pull-begäran.

## <a name="using-git-branches"></a>Använda Git-grenar

Standard grenen för PowerShell-Docs är `staging` grenen. Ändringar som görs i arbets grenar sammanfogas i `staging` grenen innan de publiceras. `staging`Grenen slås samman i `live` grenen varje veckodag med 3:00 PM (Pacific Time). `live`Grenen innehåller det innehåll som har publicerats till docs.Microsoft.com.

Innan du påbörjar ändringarna skapar du en arbets gren i din lokala kopia av PowerShell-Docs-lagringsplatsen. Var noga med att synkronisera din lokala lagrings plats innan du skapar din arbets gren när du arbetar lokalt. Arbets grenen bör skapas från en uppdatering till dags kopia av `staging` grenen.

Alla pull-begäranden bör riktas mot `staging` grenen. Skicka inte ändringar till `live` grenen.
Ändringar som görs i `staging` grenen sammanfogas i `live` och skriver över eventuella ändringar som gjorts i `live` .

## <a name="make-the-pull-request-process-work-better-for-everyone"></a>Gör så att pull-begäran fungerar bättre för alla

Den enklare och mer fokuserade du kan göra din PR, desto snabbare kan du granska och slå samman.

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a>Undvik pull-begäranden som uppdaterar ett stort antal filer eller innehåller orelaterade ändringar

Undvik att skapa pull som innehåller orelaterade ändringar. Olika små uppdateringar i befintliga artiklar från nya artiklar eller större omskrivningar. Arbeta på dessa ändringar i olika arbetsflöden.

Mass ändringar skapa pull med ett stort antal ändrade filer. Begränsa din pull-begäran till högst 50 ändrade filer. Stora pull-begäranden är svåra att granska och är mer benägna att innehålla fel.

### <a name="renaming-or-deleting-files"></a>Byta namn på eller ta bort filer

När du byter namn på eller tar bort filer, måste det finnas ett problem som är kopplat till PR. Det här problemet måste diskutera behovet av att byta namn på eller ta bort filerna.

Undvik att blanda innehålls tillägg eller ändra med fil namn och borttagningar. Alla filer som har bytt namn eller tas bort måste läggas till i den globala omdirigerings filen. Uppdatera eventuella filer som länkar till det omdöpta eller borttagna innehållet, inklusive eventuella TOC-filer, om det är möjligt.

## <a name="docs-pr-validation-service"></a>Docs PR-valideringstjänst

Verifierings tjänsten för dokument PR är en GitHub-app som kör verifierings regler på dina ändringar. Du måste åtgärda eventuella fel eller varningar som rapporter ATS av validerings tjänsten.

Följande beteende kommer att visas:

1. Du skickar en PR.
1. I GitHub-kommentaren som visar statusen för din PR ser du statusen "checkar" aktiverade på lagrings platsen. I det här exemplet finns det två kontroller aktiverade, "commit Validation" och "openpublishing. Build":

   ![validerings status-vissa kontroller misslyckades](media/pull-requests/validation-failed.png)

   Bygget kan klara även om bekräftelse valideringen Miss lyckas.

1. Klicka på **Details** (Detaljerad information) om du vill ha mer information.
1. På sidan Details (Detaljerad information) visas alla valideringskontroller som har misslyckats och information om hur du åtgärdar problemen.
1. När verifieringen lyckas läggs följande kommentar till i pull-begäran:

   ![Validerings status: lyckad](media/pull-requests/build-validation.png)

> [!NOTE]
> Om du är en extern deltagare (inte en Microsoft-anställd) har du inte åtkomst till de detaljerade build-rapporterna eller för hands versions länkar.

När PR granskas kan du bli ombedd att göra ändringar eller åtgärda varnings meddelanden. PowerShell-Docss teamet kan hjälpa dig att förstå verifierings fel och redaktionella krav.

## <a name="next-steps"></a>Nästa steg

[Stilguide för PowerShell-Docs](powershell-style-guide.md)

## <a name="additional-resources"></a>Ytterligare resurser

[Så här hanterar vi pull-begäranden](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
