---
title: Så här uppdaterar du hjälpfiler | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561398"
---
# <a name="how-to-update-help-files"></a>Uppdatera hjälpfiler

I det här avsnittet beskrivs hur du uppdaterar hjälpfiler för en modul som stöder uppdaterbar hjälp.

## <a name="updating-help-files"></a>Uppdaterar hjälpfiler

Det finns många anledningar till att uppdatera hjälpfiler, till exempel korrigera fel, för att klargöra ett koncept, besvara en vanlig fråga, lägga till nya filer eller lägga till nya och bättre exempel.

Så här uppdaterar du en hjälp fil:

1. Ändra filerna.

2. Översätt filerna till andra användar gränssnitts kulturer.

3. Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje användar gränssnitts kultur.

4. Validera filerna mot XML-schemat.

5. Återskapa CAB-filerna för varje användar gränssnitts kultur.

6. I XML-filen HelpInfo ökar du versions numret för CAB-filen för varje GRÄNSSNITTs kultur.

7. Överför de nya CAB-filerna till den plats som anges av värdet för **HelpContentUri** -elementet i HelpInfo XML-filen. Ersätt de äldre CAB-filerna med de nya CAB-filerna.

8. Ladda upp den uppdaterade HelpInfo XML-filen till den plats som anges av **HelpInfoUri** -nyckeln i modul manifestet. Ersätt den äldre HelpInfo XML-filen med den nya filen.
