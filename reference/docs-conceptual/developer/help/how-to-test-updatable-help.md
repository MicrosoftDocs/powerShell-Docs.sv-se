---
title: Testa uppdateringsbar hjälp
ms.date: 09/12/2016
ms.openlocfilehash: 0602349f853fddd0cadae545eaf0302c150e3a28
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892973"
---
# <a name="how-to-test-updatable-help"></a>Testa uppdateringsbar hjälp

I det här avsnittet beskrivs metoder för att testa uppdaterings bara hjälp för en modul.

## <a name="using-verbose-to-detect-errors"></a>Använda utförlig för att identifiera fel

När du har laddat upp XML-HelpInfo och CAB-filerna för modulen testar du filerna genom att köra ett [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kommando med **utförlig** parameter. Den **utförliga** parametern styrs `Update-Help` för att rapportera de viktiga stegen i sina åtgärder, från att läsa **HelpInfoUri** -nyckeln i modulen manifest för att validera filtyper i den uppackade CAB-filen och placera filerna i den språkspecifika modulens katalog.

När alla utförliga meddelanden har åtgärd ATS kan du köra ett `Update-Help` kommando med **fel söknings** parametern.
Den här parametern ska identifiera eventuella återstående problem med de uppdateringsfiler som kan uppdateras.
