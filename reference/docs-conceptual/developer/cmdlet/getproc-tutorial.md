---
title: GetProc-självstudie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355533"
---
# <a name="getproc-tutorial"></a>Självstudie om GetProc

Det här avsnittet innehåller en själv studie kurs om hur du skapar en get-proc-cmdlet som liknar cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) som tillhandahålls av Windows PowerShell. Den här självstudien innehåller fragment med kod som illustrerar hur cmdlets implementeras och en förklaring av koden.

## <a name="topics-in-this-tutorial"></a>Avsnitt i den här självstudien

Avsnitten i den här självstudien är utformade för att läsas sekventiellt, med varje ämne som bygger på vad som diskuterades i föregående avsnitt.

[Skapa en cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md) I det här avsnittet beskrivs hur du skapar en-cmdlet som hämtar information från den lokala datorn utan att använda parametrar, och sedan skriver informationen till pipelinen.

[Lägga till parametrar som bearbetar kommando rads indatatyper](./adding-parameters-that-process-command-line-input.md) I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-proc så att cmdleten kan bearbeta indatatyper baserat på explicita objekt som skickas till cmdleten. Implementeringen som beskrivs här hämtar processer baserat på deras namn och skriver sedan informationen till pipelinen.

[Lägga till parametrar som bearbetar pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md) I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-proc så att cmdleten kan bearbeta objekt som skickas till den via pipelinen. Implementerings-cmdleten som beskrivs här hämtar processer baserat på objekt som skickas till cmdleten och skriver sedan informationen till pipelinen.

[Lägga till fel rapportering som inte avslutas till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) I det här avsnittet beskrivs hur du lägger till fel rapportering som inte avslutas till en cmdlet. Implementeringen som beskrivs här identifierar fel som inträffar när indata bearbetas och en felpost skrivs till fel strömmen.

## <a name="see-also"></a>Se även

[Skapa en cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md)

[Lägga till parametrar som bearbetar kommando rads indatatyper](./adding-parameters-that-process-command-line-input.md)

[Lägga till parametrar som bearbetar pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md)

[Lägga till fel rapportering som inte avslutas till din cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
