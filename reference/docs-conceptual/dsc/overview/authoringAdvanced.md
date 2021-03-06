---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Förstå DSC-rollen i en CI/CD-pipeline
description: I den här artikeln beskrivs vilka typer av metoder som är tillgängliga för att kombinera konfigurationer och resurser i en CI/CD-pipeline.
ms.openlocfilehash: 8d06b86724eb25e657687e6518c01bb29d984264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647032"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>Förstå DSC-rollen i en CI/CD-pipeline

I den här artikeln beskrivs vilka typer av metoder som är tillgängliga för att kombinera konfigurationer och resurser.
Målet för varje scenario är detsamma, för att minska komplexiteten när flera konfigurationer föredras för att uppnå ett slut tillstånd för Server distribution. Ett exempel på detta är flera team som bidrar till resultatet av en Server distribution, till exempel en program ägare som upprätthåller program tillstånd och ett centralt team som släpper ut ändringar i säkerhets bas linjerna. Olika delarna för varje metod inklusive de fördelar och risker som beskrivs här.

![Process flöde för en CI/CD-pipeline](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Typer av tekniker för samarbets redigering

Det finns två lösningar som är inbyggda i lokala Configuration Manager för att aktivera det här konceptet:

|        Koncept         |                    Detaljerad information                     |
| ---------------------- | ----------------------------------------------------------- |
| Partiella konfigurationer | [Dokumentation](../pull-server/partialConfigs.md)           |
| Sammansatta resurser    | [Dokumentation](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a>Förstå påverkan av varje metod

Du kan använda någon av dessa lösningar för att hantera resultatet av en Server distribution. Det finns dock betydande skillnader i effekten av att använda varje metod.

## <a name="partial-configurations"></a>Partiella konfigurationer

När du använder partiella konfigurationer konfigureras lokala Configuration Manager för att hantera flera konfigurationer oberoende av varandra. Konfigurationer kompileras oberoende och tilldelas sedan till noden. Detta kräver att LCM konfigureras i förväg med namnet på varje konfiguration.

![Diagram över partiella konfigurationer](media/authoringAdvanced/PartialConfiguration.jpg)

Partiella konfigurationer ger två eller fler team fullständig kontroll över konfigurationen av en server, ofta utan fördelarna med kommunikation eller samarbete.

Kunderna har fått feedback om att detta kan leda till resurs konflikter, oavsiktliga åsidosättningar och i slut ändan av den verkliga konfigurations kontrollen för till gången.

Kunder har dessutom fått feedback om att när du använder den här modellen, är varje ändring av team konfigurations ändringar troligen inte helt testade genom en versions pipeline, vilket leder till oväntade resultat i produktionen.

**Det är viktigt att en enda pipeline används för att utvärdera alla ändringar som släpps till servrar.**

I bilden nedan släpper team B sin del konfiguration till Team A. Team A kör sedan sina tester mot en server med båda konfigurationerna applicerade. I den här modellen har endast en myndighet behörighet att göra ändringar i produktionen.

![Diagram över en delvis enskild pipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

När ändringar krävs från Team B bör de skicka in en pull-begäran mot gruppens käll kontroll miljö. Team A granskar sedan ändringarna med test automatisering och släpp till produktion när det är säkert att ändringarna inte orsakar fel i de program eller tjänster som servern är värd för.

## <a name="composite-resources"></a>Sammansatta resurser

En sammansatt resurs är helt enkelt en DSC-konfiguration som paketeras som en resurs. Det finns inga särskilda krav för att konfigurera LCM för att godkänna sammansatta resurser. Resurserna används i en ny konfiguration och ett enda kompilerings resultat i en MOF-fil.

![Diagram över en sammansatt resurs](media/authoringAdvanced/CompositeResource.jpg)

Det finns två vanliga scenarier för sammansatta resurser. Det första är att minska komplexiteten och abstrakta unika begrepp. Det andra är att tillåta att bas linjer paketeras för att en program grupp ska kunna distribueras genom sin versions pipeline till produktion när alla tester har slutförts.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

Sammansatta resurser befordrar både komposition och samarbete med en pipeline medan man skapar drifts löp tid.

Du kanske redan använder sammansatta resurser utan att realisera den. Ett exempel är **ServiceSet** .
Den här resursen hanterar statusen för flera Windows-tjänster utan att lista dem separat. Egenskapen Name accepterar en sträng mat ris som anger namnet på varje tjänst. När konfigurationen kompileras innehåller MOF ett unikt tjänst avsnitt för varje namn som skickas till ServiceSet.

Organisationer kan ha "agenter" eller "mellanprogram" som ska installeras på alla servrar. En sammansatt resurs är det bästa svaret på att hantera beroenden, installation och konfiguration av sådana verktyg och verktyg.

Den person eller det team som ansvarar för lösningar som sträcker sig över flera servrar redigerar en konfiguration som innehåller deras krav. Därefter paketeras konfigurationen som en sammansatt resurs med hjälp av anvisningarna i den sammansatta resurs dokumentationen. Slutligen bör den nya sammansatta resursen publiceras på en plats, till exempel en fil resurs eller ett NuGet-flöde där program team kan använda den i sina konfigurationer.

Varje gången gruppen frigör en ny version, ökar versions numret i modulens manifest för sin sammansatta resurs. Program teamen innehåller den sammansatta resursen i konfigurationen som de skapar för att hantera program beroenden. När drift-/säkerhets teamen släpper en ny version av sin resurs, meddelar de program teamen om en ny ändring.

Program teamen kan utlösa en version till produktion där den enda ändringen är till bas linjer.
Detta ger dock en möjlighet att utvärdera program som påverkar risken för avbrott i tjänsten.

> [!NOTE]
> Feedback om användningen av sammansatta resurser har inkluderat Criticism som gör att ändringar kräver kompilering och frisläppning av en ny MOF. Det här är avsiktligt. Varje ny konfigurations utgåva bör innehålla en statisk referens till en speciell version av varje resurs och bör verifieras av tester innan de når till produktions serverns noder. Processen för att testa och släppa ändringar från käll kontrollen skapar en säker miljö för att släppa ändringar i små och ofta förekommande batchar.

Mer information om hur du använder versions pipelines för att hantera kärn infrastrukturen finns i fakta bladet [version: versions pipeline](../further-reading/whitepapers.md).
