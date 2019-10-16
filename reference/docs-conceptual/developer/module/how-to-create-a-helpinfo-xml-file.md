---
title: Så här skapar du en HelpInfo XML-fil | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357549"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Skapa en HelpInfo-XML-fil

I det här avsnittet beskrivs hur du skapar och fyller i en hjälp informations fil, som kallas för en "HelpInfo XML-fil", för den uppdaterings bara hjälp funktionen i Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Översikt över HelpInfo XML-fil

XML-filen HelpInfo är den främsta informations källan om uppdaterings bar hjälp för modulen. Den innehåller platsen för hjälpfilerna för modulerna, de användar gränssnitts kulturer som stöds och de versions nummer som uppdaterings bara hjälp använder för att avgöra om användaren har de senaste hjälpfilerna.

Varje modul har bara en HelpInfo XML-fil, även om modulen innehåller flera hjälpfiler för flera användar gränssnitts kulturer. Modulens författare skapar XML-filen HelpInfo och placerar den på Internet-platsen som anges av **HelpInfoUri** -nyckeln i modul manifestet. När modulens hjälpfiler uppdateras och överförs, uppdaterar modulen HelpInfo XML-filen och ersätter den ursprungliga HelpInfo XML-filen med den nya versionen.

Det är viktigt att XML-filen HelpInfo underhålls noggrant. Om du laddar upp nya filer, men glömmer att öka versions numren, kommer uppdaterings bara hjälp att ladda ned de nya filerna till användarnas datorer. Om du lägger till hjälpfiler för en ny kultur för användar gränssnittet, men inte uppdaterar XML-HelpInfo eller placerar den på rätt plats, kommer uppdaterings bara hjälp att inte hämta de nya filerna.

## <a name="in-this-section"></a>I detta avsnitt

Det här avsnittet innehåller följande ämnen.

- [HelpInfo XML-schema](./helpinfo-xml-schema.md)

- [HelpInfo XML-exempel fil](./helpinfo-xml-sample-file.md)

- [Så här namnger du en HelpInfo XML-fil](./how-to-name-a-helpinfo-xml-file.md)

- [Så här ställer du in versions nummer för HelpInfo XML](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Se även

[Stöd för uppdaterbar hjälp](./supporting-updatable-help.md)