---
title: GetProc självstudien | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851333"
---
# <a name="getproc-tutorial"></a>Självstudie om GetProc

Det här avsnittet innehåller en självstudie för att skapa en cmdlet Get-processen som liknar den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet som tillhandahålls av Windows PowerShell. Den här självstudien innehåller delar av kod som illustrerar hur cmdletar implementeras och en förklaring av koden.

## <a name="topics-in-this-tutorial"></a>Avsnitt i den här självstudien

Ämnena i den här självstudien är avsedda att läsas sekventiellt, med varje avsnitt som bygger på vad som beskrevs i föregående avsnitt.

[Skapa en Cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md) i det här avsnittet beskriver hur du skapar en cmdlet som hämtar information från den lokala datorn utan att använda parametrar och skriver informationen till pipelinen.

[Att lägga till parametrar som processen Command-Line inkommande](./adding-parameters-that-process-command-line-input.md) det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-processen så att cmdleten kan bearbeta indata som baseras på explicita objekt skickades till cmdlet: en. Implementeringen som beskrivs hämtar här processer baserat på deras namn och skriver informationen till pipelinen.

[Att lägga till parametrar som indata från Pipeline processen](./adding-parameters-that-process-pipeline-input.md) det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-processen så att cmdleten kan bearbeta objekt som skickas till den via pipelinen. Cmdleten implementeringen som beskrivs hämtar här processer baserat på objekt som överförs till cmdlet: en och skriver informationen till pipelinen.

[Att lägga till oändliga felrapportering i din Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) det här avsnittet beskrivs hur du lägger till oändliga fel som rapporterar till en cmdlet. Implementeringen som beskrivs här identifierar oändliga fel som inträffar när indata och skriver en Felpost till felströmmen.

## <a name="see-also"></a>Se även

[Skapa en Cmdlet utan parametrar](./creating-a-cmdlet-without-parameters.md)

[Att lägga till parametrar som bearbetar av kommandoraden](./adding-parameters-that-process-command-line-input.md)

[Att lägga till parametrar som indata för Process-pipelinen](./adding-parameters-that-process-pipeline-input.md)

[Att lägga till oändliga felrapportering i cmdlet:](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
