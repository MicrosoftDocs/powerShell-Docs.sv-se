---
title: Så här hanterar vi problem
description: Den här artikeln förklarar hur PowerShell-Docs-teamet hanterar problem.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352710"
---
# <a name="how-we-manage-issues"></a>Så här hanterar vi problem

Den här artikeln dokumenterar vi hur vi hanterar problem i PowerShell-Docs lagrings platsen. Den här artikeln är utformad för att vara ett jobb stöd för medlemmar i PowerShell-Docss teamet. Den publiceras här för att tillhandahålla process genomskinlighet för våra offentliga deltagare.

## <a name="sources-of-issues"></a>Problem källor

- Community-deltagare
- Interna bidrags givare
- Avskrifter av kommentarer från sociala media-kanaler
- Feedback via feedback-formuläret för dokument

## <a name="response-time-targets"></a>Svars tids mål

80% av de nya problemen är stängda inom tre arbets dagar.

- Prioriteras – 1 arbets dagar
- Korrigera eller ändra 10 arbets dagar

### <a name="labeling--milestones"></a>Etikettera & mil stolpar

#### <a name="label-types"></a>Etikett typer

|   Typ   | Beskrivning                                                         |
| -------- | ------------------------------------------------------------------- |
| Område     | Används för att ange vilken del av PowerShell eller dokument som problemet diskuterar.<br>Användbart för funktions ägare för att hitta problem med deras funktion. |
| Problem    | Anger typen av problem                                         |
| Prioritet | Anger prioriteten för problemet. Värde intervall 0 (högt)-4 (låg)  |
| Status   | Anger status för arbets uppgiften eller varför den stängdes          |
| Tagga      | Etiketter som används för att lägga till ytterligare klassificering                        |
| Väntar  | Indikerar att vi väntar på någon eller någon annan händelse         |

#### <a name="milestones"></a>Milstolpar

Problem och pull ska taggas med lämplig mil stolpe. Om problemet inte gäller för en speciell version används ingen mil stolpe. Pull och relaterade problem för ändringar som ännu inte har sammanfogats till PowerShell-kodbasen bör tilldelas till den **framtida** mil stolpen. När kod ändringen har slagits samman ändrar du mil stolpen till rätt version.

|    Gränser     |                    Beskrivning                     |
| ---------------- | -------------------------------------------------- |
| 7.0.0            | Arbets objekt som rör PowerShell 7,0               |
| 7.1.0            | Arbets objekt som rör PowerShell 7,1               |
| 7.2.0            | Arbets objekt som rör PowerShell 7,2               |
| I framtiden           | Arbets uppgifter en framtida version av PowerShell          |

## <a name="triage-process"></a>Prioritering process

I PowerShell-dokumentets grupp medlemmar granskas problemen varje dag och prioritering nya problem när de tas emot. Teamet uppfyller vecko kraven för att diskutera problem som behöver prioritering eller vara olösta.

### <a name="misplaced-product-feedback"></a>Felplacerad produkt feedback

- Ange en kommentar som omdirigerar kunden till rätt feedback-kanal.
- Valfritt: kopiera problemet till lämplig plats för produkt feedback, Lägg till en länk till det kopierade objektet och Stäng problemet. Kopiera inte problem till UserVoice.

  Standard platsen för PowerShell-problem är [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) .

  Följande ämnes områden har olika platser för problem:

  | Ämnen |                                                     URL för feedback för produkt                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | dsc      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | galleri  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | Jea      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | WMF      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a>Supportförfrågningar

- Om support frågan är enkel, kan du besvara den politely och stänga problemet.
- Om frågan är mer komplicerad eller om du svarar på fler frågor kan du omdirigera dem till forum och support kanaler. Föreslagen text för omdirigering till Forum:

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a>Regler för uppförande av fel

- Redigera problemet om du vill ta bort stötande innehåll, om det behövs.
- Ange en kommentar som visar att problemet är skräp post, Stäng problemet och lås det för att förhindra ytterligare kommentarer.
- Varje överträdelse bör diskuteras i varje veckas prioritering för att fastställa behovet av ytterligare åtgärd (rapportera till GitHub eller Microsoft legal).
