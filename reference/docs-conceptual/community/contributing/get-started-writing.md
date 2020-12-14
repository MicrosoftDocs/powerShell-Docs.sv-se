---
title: Kom igång och bidra till PowerShell-dokumentationen
description: Den här artikeln är en översikt över hur du kommer igång med att bidra till PowerShell-dokumentationen.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352703"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Kom igång och bidra till PowerShell-dokumentationen

Den här artikeln är en översikt över hur du kommer igång med att bidra till PowerShell-dokumentationen.

## <a name="powershell-docs-structure"></a>PowerShell-Docs struktur

[Databasen PowerShell-dok][psdocs] är uppdelad i två grupper med innehåll: referens och koncept.

### <a name="reference-content"></a>Referensinnehåll

Referens innehållet är PowerShell-cmdlet-referensen för de cmdletar som levereras i PowerShell.
[Referensen][ref] samlas in i mapparna versioner (5,1, 7,0, 7,1 och 7,2). Det här innehållet innehåller endast cmdlet-referenser för moduler som levereras med PowerShell. Det här innehållet används också för att skapa hjälp informationen som visas av `Get-Help` cmdleten.

### <a name="conceptual-content"></a>Konceptuellt innehåll

Den konceptuella dokumentationen innehåller följande innehåll:

- Viktig information
- Installations anvisningar
- Exempel skript och instruktions artiklar
- DSC-dokumentation
- SDK-dokumentation

Den [konceptuella dokumentationen][conceptual] ordnas inte efter version. Alla artiklar visas för alla versioner av PowerShell. Vi arbetar för att skapa versions bara artiklar. När den här funktionen är tillgänglig i vår dokumentation kommer den här hand boken att uppdateras med lämplig information.

> [!NOTE]
> När en konceptuell artikel läggs till, tas bort eller ändras, måste innehålls förteckningen uppdateras och tas med i pull-begäran.

## <a name="creating-new-articles"></a>Skapa nya artiklar

Ett GitHub-problem måste skapas för alla nya dokument som du vill bidra. Sök efter befintliga problem för att se till att du inte duplicerar aktiviteter. Tilldelade problem anses vara `in progress` . Om du vill samar beta om ett problem kontaktar du personen som har tilldelats problemet.

Precis som i PowerShell [RFC-processen][rfc]skapar du ett problem innan du skriver innehållet. Problemet garanterar att du inte slösar tid och arbetar på arbete som avvisas av PowerShell-Docss teamet. Problemet gör att vi kan kontakta dig med innehålls området och var det passar i PowerShell-dokumentationen. Alla artiklar måste inkluderas i innehålls förteckningen (TOC). Den föreslagna TOC-platsen ska ingå i ärende diskussionen.

> [!NOTE]
> Innehålls förteckningen för referens innehållet genereras automatiskt av publicerings systemet. Du behöver inte uppdatera innehålls förteckningen.

## <a name="updating-existing-articles"></a>Befintliga artiklar uppdateras

I tillämpliga fall dupliceras cmdlet Reference-artiklar i alla versioner av PowerShell i den här lagrings platsen. När du rapporterar ett problem med en cmdlet-referens eller en `About_` artikel, måste du ange vilka versioner som påverkas av problemet. Issue-mallen i GitHub innehåller en check lista för versioner. Använd kryss rutorna för att ange vilka versioner av innehållet som påverkas.

Kontrol lera alla versioner av artikeln för att se om samma ändring krävs i de andra versionerna. Tillämpa lämplig ändring för varje version av filen.

## <a name="localized-content"></a>Lokaliserat innehåll

PowerShell-dokumentationen skrivs på engelska och översätts till 17 andra språk. Det engelska innehållet lagras i GitHub-lagringsplatsen med namnet `MicrosoftDocs/PowerShell-Docs` . Det lokaliserade innehållet lagras i en separat lagrings plats för varje språk. Databaserna använder samma basename men lägger till språk namnet i slutet. Innehåller till exempel `MicrosoftDocs/PowerShell-Docs.de-de` det innehåll som har översatts till tyska.

I allmänhet bör problem och ändringar skickas till den engelska lagrings platsen. Alla översättningar börjar från det engelska innehållet först. Vi använder både mänsklig och maskin översättning.

| Översättnings metod  |                              Språk                               |
| ------------------- | -------------------------------------------------------------------- |
| Mänsklig översättning   | de-DE, es-ES, fr-FR, IT-IT, ja-JP, ko-KR, pt-BR, ru-RU, zh-CN, zh-TW |
| Maskin Översättning | CS-CZ, hu-HU, nl-NL, pl-PL, pt-PT, sa-SE, tr-TR                      |

Innehållet som översätts av maskin översättning kanske inte alltid leder till rätt Word-val och grammatik. Om du hittar ett fel i översättningen för något språk, i stället för i den tekniska informationen i artikeln, öppnar du ett problem i den lokaliserade lagrings platsen. Förklara varför du tycker att översättningen är felaktig. Vårt lokaliserings team granskar och åtgärdar problemen.

## <a name="next-steps"></a>Nästa steg

Det finns två vanliga sätt att skicka ändringar i GitHub. Båda metoderna beskrivs i Central bidrags guide:

1. Du kan göra [snabba ändringar i befintliga dokument](/contribute/#quick-edits-to-existing-documents) i GitHub-webbgränssnittet.
1. Använd det [fullständiga GitHub-arbetsflödet][making-changes] för att lägga till nya artiklar, uppdatera flera filer eller andra stora ändringar.

Innan du påbörjar ändringarna bör du skapa en förgrening av PowerShell-Docs-lagringsplatsen. Ändringarna bör göras i en arbets gren i din kopia av PowerShell-dokumenten. Om du använder **Quick Edit** -metoden i GitHub hanteras dessa steg åt dig. Om du använder det **fullständiga GitHub-arbetsflödet** måste du konfigureras att [fungera lokalt][fork].

Båda metoderna slutar med att skapa en pull-begäran (PR). Mer information och bästa praxis finns i [skicka en pull-begäran](pull-requests.md) .

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
