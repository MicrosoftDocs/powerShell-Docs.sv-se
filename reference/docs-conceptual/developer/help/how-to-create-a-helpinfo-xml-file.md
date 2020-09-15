---
title: Skapa en HelpInfo-XML-fil
ms.date: 09/13/2016
ms.openlocfilehash: e395746e51309477bbcbff51b4591de3f73ce0db
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893313"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Skapa en HelpInfo-XML-fil

I det här avsnittet beskrivs hur du skapar och fyller i en hjälp informations fil, som vanligt vis kallas "HelpInfo XML-fil", för den PowerShell-baserade hjälp funktionen.

## <a name="helpinfo-xml-file-overview"></a>Översikt över HelpInfo XML-fil

XML-filen HelpInfo är den främsta informations källan om uppdaterings bar hjälp för modulen. Den innehåller platsen för hjälpfilerna för modulerna, de användar gränssnitts kulturer som stöds och de versions nummer som uppdaterings bara hjälp använder för att avgöra om användaren har de senaste hjälpfilerna.

Varje modul har bara en HelpInfo XML-fil, även om modulen innehåller flera hjälpfiler för flera användar gränssnitts kulturer. Modulens författare skapar XML-filen HelpInfo och placerar den på Internet-platsen som anges av **HelpInfoUri** -nyckeln i modul manifestet. När modulens hjälpfiler uppdateras och överförs, uppdaterar modulen HelpInfo XML-filen och ersätter den ursprungliga HelpInfo XML-filen med den nya versionen.

Det är viktigt att XML-filen HelpInfo underhålls noggrant. Om du laddar upp nya filer, men glömmer att öka versions numren, kommer uppdaterings bara hjälp att ladda ned de nya filerna till användarnas datorer. Om du lägger till hjälpfiler för en ny kultur för användar gränssnittet, men inte uppdaterar XML-HelpInfo eller placerar den på rätt plats, kommer uppdaterings bara hjälp att inte hämta de nya filerna.

## <a name="in-this-section"></a>Innehåll i det här avsnittet

Det här avsnittet innehåller följande ämnen.

- [HelpInfo-XML-schema](./helpinfo-xml-schema.md)

- [HelpInfo-XML-exempelfil](./helpinfo-xml-sample-file.md)

- [Namnge en HelpInfo-XML-fil](./how-to-name-a-helpinfo-xml-file.md)

- [Konfigurera versionsnummer för HelpInfo-XML-filer](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Se även

[Stöd för uppdateringsbar hjälp](./supporting-updatable-help.md)
