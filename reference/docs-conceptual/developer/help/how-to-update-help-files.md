---
ms.date: 09/12/2016
ms.topic: reference
title: Uppdatera hjälpfiler
description: Uppdatera hjälpfiler
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649590"
---
# <a name="how-to-update-help-files"></a>Uppdatera hjälpfiler

I det här avsnittet beskrivs hur du uppdaterar hjälpfiler för en modul som stöder uppdaterbar hjälp.

## <a name="updating-help-files"></a>Uppdaterar hjälpfiler

Det finns många anledningar till att uppdatera hjälpfiler, till exempel korrigera fel, för att klargöra ett koncept, besvara en vanlig fråga, lägga till nya filer eller lägga till nya och bättre exempel.

Så här uppdaterar du en hjälp fil:

1. Ändra filerna.
1. Översätt filerna till andra användar gränssnitts kulturer.
1. Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje användar gränssnitts kultur.
1. Validera filerna mot XML-schemat.
1. Återskapa CAB-filerna för varje användar gränssnitts kultur.
1. I XML-filen HelpInfo ökar du versions numret för CAB-filen för varje GRÄNSSNITTs kultur.
1. Överför de nya CAB-filerna till den plats som anges av värdet för **HelpContentUri** -elementet i HelpInfo XML-filen. Ersätt de äldre CAB-filerna med de nya CAB-filerna.
1. Ladda upp den uppdaterade HelpInfo XML-filen till den plats som anges av **HelpInfoUri** -nyckeln i modul manifestet. Ersätt den äldre HelpInfo XML-filen med den nya filen.
