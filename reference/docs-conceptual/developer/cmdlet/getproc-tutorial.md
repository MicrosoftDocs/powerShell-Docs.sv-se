---
ms.date: 09/13/2016
ms.topic: reference
title: Självstudie om GetProc
description: Självstudie om GetProc
ms.openlocfilehash: 9379e791dd5361fcf5b79061bf0a601ebeb84f42
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652780"
---
# <a name="getproc-tutorial"></a>Självstudie om GetProc

Det här avsnittet innehåller en själv studie kurs om hur du skapar en Get-Proc-cmdlet som liknar cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) som tillhandahålls av Windows PowerShell. Den här självstudien innehåller fragment med kod som illustrerar hur cmdlets implementeras och en förklaring av koden.

## <a name="topics-in-this-tutorial"></a>Avsnitt i den här självstudien

Avsnitten i den här självstudien är utformade för att läsas sekventiellt, med varje ämne som bygger på vad som diskuterades i föregående avsnitt.

[Skapa en cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som hämtar information från den lokala datorn utan att använda parametrar, och sedan skriver informationen till pipelinen.

[Lägga till parametrar som bearbetar Command-Line-Indatatyp](./adding-parameters-that-process-command-line-input.md) I det här avsnittet beskrivs hur du lägger till en parameter i Get-Proc cmdlet så att cmdleten kan bearbeta indatatyper baserat på explicita objekt som skickas till cmdleten. Implementeringen som beskrivs här hämtar processer baserat på deras namn och skriver sedan informationen till pipelinen.

[Lägga till parametrar som bearbetar pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md) I det här avsnittet beskrivs hur du lägger till en parameter i Get-Proc-cmdleten så att cmdleten kan bearbeta objekt som skickas till den via pipelinen. Implementerings-cmdleten som beskrivs här hämtar processer baserat på objekt som skickas till cmdleten och skriver sedan informationen till pipelinen.

[Lägga till fel rapportering som inte avslutas till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) I det här avsnittet beskrivs hur du lägger till fel rapportering som inte avslutas till en cmdlet. Implementeringen som beskrivs här identifierar fel som inträffar när indata bearbetas och en felpost skrivs till fel strömmen.

## <a name="see-also"></a>Se även

[Skapa en cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md)

[Lägga till parametrar som bearbetar Command-Line-Indatatyp](./adding-parameters-that-process-command-line-input.md)

[Lägga till parametrar som bearbetar pipelineindata](./adding-parameters-that-process-pipeline-input.md)

[Lägga till fel rapportering som inte avslutas till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
