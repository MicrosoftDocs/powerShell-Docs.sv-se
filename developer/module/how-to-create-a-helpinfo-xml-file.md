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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844900"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Skapa en HelpInfo-XML-fil

Detta avsnitt i det här avsnittet beskrivs hur du skapar och fyller ett information hjälpfilen kallas en ”HelpInfo XML-fil”, för funktionen Windows PowerShell uppdateringsbar hjälp.

## <a name="helpinfo-xml-file-overview"></a>Översikt över HelpInfo XML-fil

HelpInfo XML-filen är den primära källan för information om uppdateringsbar hjälp för modulen. Den innehåller platsen för hjälpfilerna för moduler, kulturer som stöds Användargränssnittet och versionsnumren som uppdateringsbar hjälp använder för att avgöra om användaren har de senaste hjälpfilerna.

Varje modul har bara ett HelpInfo XML-fil, även om modulen innehåller flera hjälpfilerna för flera Användargränssnittet kulturer. Modulägaren skapar HelpInfo XML-filen och placerar den i den Internet-plats som anges av den **HelpInfoUri** nyckeln i modulmanifestet. När modulen hjälpfilerna är uppdaterade och överförts, modulägaren uppdaterar HelpInfo XML-filen och ersätter den ursprungliga HelpInfo XML-filen med den nya versionen.

Det är viktigt att upprätthålls noggrant HelpInfo XML-filen. Om du överför nya filer, men glömmer att öka versionsnumren, hämtas uppdateringsbar hjälp inte de nya filerna till användarna. Om du lägger till hjälpfilerna för en ny UI-kultur, men inte uppdatera HelpInfo XML-filen eller placera den på rätt plats, hämta uppdateringsbar hjälp inte de nya filerna skapas.

## <a name="in-this-section"></a>I detta avsnitt

Det här avsnittet innehåller följande ämnen.

- [HelpInfo XML-Schema](./helpinfo-xml-schema.md)

- [HelpInfo XML-exempelfilen](./helpinfo-xml-sample-file.md)

- [Hur du namnger en HelpInfo XML-fil](./how-to-name-a-helpinfo-xml-file.md)

- [Hur du ställer in HelpInfo XML-versionsnummer](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Se även

[Stöd för uppdateringsbar hjälp](./supporting-updatable-help.md)