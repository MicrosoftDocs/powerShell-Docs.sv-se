---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Avancerad DSC-redigering för sammansättning och samarbete
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405320"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a>Avancerad DSC-redigering för sammansättning och samarbete

Den här artikeln beskrivs olika metoder som är tillgängliga för att kombinera konfigurationer och resurser.
Målet för varje scenario är samma, minska komplexiteten när flera konfigurationer är lämpligt att nå slutet distributionstillstånd för en server.
Ett exempel på detta är flera team som bidrar till resultatet av en serverdistribution, till exempel en programägaren programtillståndet och ett centralt team lanserar ändringar i säkerheten.
Här beskrivs de olika delarna i varje metod, inklusive fördelar och risker.

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Typer av samarbetsfunktioner redigering tekniker

Det finns två lösningar som skapats till lokala Configuration Manager för att aktivera detta begrepp:

| Begrepp | Detaljerad Information
|-|-
| Partiella konfigurationer | [Dokumentation](../pull-server/partialConfigs.md)
| Sammansatta resurser | [Dokumentation](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Förstå effekten av varje metod

Någon av dessa lösningar kan användas för att hantera resultatet av en server-distribution.
Det finns betydande skillnader i effekten av att använda varje metod.

## <a name="partial-configurations"></a>Partiella konfigurationer

När du använder partiella konfigurationer, har Local Configuration Manager konfigurerats för att hantera konfigurationer med flera oberoende av varandra.
Konfigurationer kompileras oberoende av varandra och sedan tilldelad till noden.
Detta kräver LCM konfigureras i förväg med namnet på varje konfiguration.

![PartialConfiguration](../images/PartialConfiguration.jpg)

Partiella konfigurationer ange två eller fler, teams fullständig kontroll över konfigurationen för en server, ofta utan kommunikations- eller samarbetstjänster.

Kunder har angett feedback som detta kan leda till konflikter, oavsiktlig åsidosättningar och i slutänden förlust av SANT Konfigurationskontroll av tillgången.

Kunder har dessutom som feedback att varje styra team konfigurationsändringar är sannolikt inte kommer att testas helt via en releasepipeline när du använder den här modellen, vilket leder till oväntade resultat i produktion.

**Det är viktigt att en enda pipeline kan användas för att utvärdera alla ändringar versionen till servrar.**

På bilden nedan Team B släpper sina partiell konfiguration till teamet A. Team A och kör sina tester mot en server med båda konfigurationer som används.
I den här modellen har endast en utfärdaren behörighet att göra ändringar i produktion.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

När det krävs ändringar från teamet B, bör de skicka en Pull-begäran mot Team A: s källmiljö för kontrollen.
Grupp A skulle sedan granska ändringarna med automatiserad testning och släpp till produktion när det inte är säker på att ändringarna inte orsakar fel i program eller tjänster som hanteras av servern.

## <a name="composite-resources"></a>Sammansatta resurser

En sammansatt resurs är helt enkelt en DSC-konfiguration som paketerad som en resurs.
Det finns inga särskilda krav för att konfigurera LCM att acceptera sammansatta resurser.
Resurserna som används i en ny konfiguration och en enda sammanställning resulterar i en MOF-filen.

![CompositeResource](../images/CompositeResource.jpg)

Det finns två vanliga scenarier för sammansatta resurser.
Först är att minska komplexiteten och abstrakt unika begrepp.
Andra är att tillåta baslinjer som ska paketeras för ett program-teamet på ett säkert sätt distribuerar via sina releasepipeline till produktion när du har klarat alla tester.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Sammansatta resurser för enklare både sammansättning och samarbete med hjälp av en pipeline när du skapar operativa mognad

Du kanske redan använder sammansatta resurser utan att märker det.
Ett exempel är **ServiceSet**.
Den här resursen hanterar tillståndet för flera Windows-tjänster utan att skriva dem individuellt.
Namnegenskapen accepterar en matris med strängar att ange namnet på varje tjänst.
När konfigurationen kompileras innehåller MOF en unik Service-avsnittet för var och en av de namn som skickats till ServiceSet.

Organisationer kan ha ”agenter” eller ”mellanprogram” som ska installeras på varje server.
En sammansatt resurs är det bästa svaret för att hantera beroenden, installationen och konfigurationen av verktyg och hjälpmedel.

Den person eller grupp som ansvarar för lösningar som sträcker sig över flera servrar skapar du en konfiguration som innehåller deras krav.
Sedan skulle konfigurationen vara paketerad som sammansatta resurser genom att använda instruktionerna i dokumentationen till sammansatta resource.
Slutligen den nya sammansatta resursen ska publiceras till en plats, till exempel en filresurs eller NuGet flöde där applikationsteam kan använda den i sina konfigurationer.

Varje gång som teamet släpper en ny version, skulle de öka versionsnumret i modulmanifestet för sina sammansatta resursen.
Programteam innehåller sammansatta resurs i konfigurationen som de skapar för att hantera beroenden.
När Operations/Security Team släpper en ny version av resursen, meddela de programteam av en ny ändring.

Programteam kan utlöser en släppning till produktion där den enda förändringen är att baslinjer.
Det ger dock en möjlighet att utvärdera påverkan på program innan du risken för avbrott i tjänsten.

Obs! – Feedback om användningen av sammansatta resurser har inkluderat kritik för att ändringarna kräver när koden kompileras och lanserar en ny MOF.
Det här är avsiktligt.
Varje ny version av configuration bör innehålla en statisk referens till en specifik version av varje resurs och bör verifieras genom tester innan de når produktionen servernoder.
Hur du testar och publicerar ändringar från källkontroll skapar en säker miljö för att frisläppa ändring i små och ofta batchar.

Mer information om hur du använder distributions-pipelines för att hantera grundläggande infrastruktur finns i faktabladet: [Pipeline-modellen versionen](../further-reading/whitepapers.md).
