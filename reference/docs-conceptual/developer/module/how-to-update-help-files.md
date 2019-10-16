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
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357423"
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