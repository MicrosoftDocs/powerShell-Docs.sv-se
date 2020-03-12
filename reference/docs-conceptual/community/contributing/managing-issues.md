---
title: Så här hanterar vi problem
description: Den här artikeln förklarar hur PowerShell-dokument-teamet hanterar pull-begäranden.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078537"
---
# <a name="how-we-manage-issues"></a>Så här hanterar vi problem

Den här artikeln dokumenterar vi hur vi hanterar problem i PowerShell-dok lagrings platsen. Den här artikeln är utformad för att vara ett jobb stöd för medlemmar i gruppen PowerShell-dok. Den publiceras här för att tillhandahålla process genomskinlighet för våra offentliga deltagare.

## <a name="sources-of-issues"></a>Problem källor

- Community-deltagare
- Interna bidrags givare
- Avskrifter av kommentarer från sociala media-kanaler
- Feedback via feedback-formuläret för dokument

## <a name="response-time-targets"></a>Svars tids mål

- Prioriteras – 5 arbets dagar
- Åtgärda eller ändra inga specifika mål – bästa möjliga ansträngning

### <a name="labeling--milestones"></a>Etikettera & mil stolpar

#### <a name="label-types"></a>Etikett typer

|Protokollprefixet  | Beskrivning                                                         |
|------- | --------------------------------------------------------------------|
|Område    | Används för att ange vilken del av PowerShell eller dokument som problemet diskuterar.<br>Användbart för funktions ägare för att hitta problem med deras funktion.|
|PRI     | Används för att ange prioriteten för problemet. Värde intervall 0-4.        |
|Problem   | Används för att klassificera typen av feedback för problem                     |
|Granska  | Används för problem som kräver ytterligare granskning av teamet              |
|Status  | Används för att ange arbets objektets status                        |
|Väntar | Används för att indikera att vi väntar på något                   |

#### <a name="milestones"></a>Mil stolpar

Problem och pull ska taggas med lämplig mil stolpe. Om problemet inte är avsett för en viss version, används ingen mil stolpe. Problem med dokument pull för ändringar som ännu inte har slagits samman i PowerShell-kodbasen bör tilldelas till den **framtida** mil stolpen. När kod ändringen har slagits samman ändrar du mil stolpen till rätt version.

|    Gränser     |                    Beskrivning                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | Arbets objekt som rör PowerShell 6,0 till och med 6.2. x |
| 7.0.0            | Arbets objekt som rör PowerShell 7,0               |
| 7.1.0            | Arbets objekt som rör PowerShell 7,1               |
| längre           | Arbets uppgifter en framtida version av PowerShell          |
| PSReadline – vNext | Arbets objekt en framtida version av PSReadline          |

## <a name="triage-process"></a>Prioritering process

Gruppen PowerShell-dokument uppfyller en gång per vecka för att diskutera eventuella problem som har lagts till sedan förra mötet. Ett problem anses ha prioriteras när etiketter har tilldelats eller en ägare har tilldelats. Grupp medlemmar i PowerShell-teamet uppmanas att granska problemen varje dag och prioritering nya problem när de tas emot. Det veckovis prioritering mötet kan sedan användas för att diskutera de nya problemen mer detaljerat efter behov.

### <a name="misplaced-product-feedback"></a>Felplacerad produkt feedback

- Ange en kommentar för kunden som visar att den är produkt kommentarer och ange en länk till lämplig feedback-kanal.
- Valfritt: kopiera problemet till lämplig plats för produkt feedback, Lägg till en länk till det kopierade objektet och Stäng problemet. Kopiera inte problem till UserVoice.

  | Dokument uppsättning    | URL för feedback för produkt                                         |
  | --------- | ------------------------------------------------------------ |
  | utvecklarläget | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | DSC       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | formatmall   | https://github.com/powershell/powershellgallery/issues/new   |
  | Jea       | https://github.com/powershell/jea/issues/new                 |
  | Referens | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | WMF       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a>Support förfrågningar

- Om support frågan är enkel, kan du besvara den politely och stänga problemet.
- Om frågan är mer komplicerad eller om du svarar på fler frågor kan du omdirigera dem till forum och support kanaler. Föreslagen text för omdirigering till Forum:

    > Detta är inte rätt forum för dessa typer av frågor. Försök att publicera din fråga i ett forum för Community-support. En lista över community-forum finns i: https://docs.microsoft.com/powershell/scripting/community/community-support

### <a name="code-of-conduct-violations"></a>Regler för uppförande av fel

- Redigera problemet om du vill ta bort stötande innehåll, om det behövs.
- Ange en kommentar som visar att problemet är skräp post, Stäng problemet och lås det för att förhindra ytterligare kommentarer.
- Varje förekomst av detta bör diskuteras i varje veckas prioritering för att fastställa behovet av ytterligare åtgärd (rapportera till GitHub eller Microsoft legal).
