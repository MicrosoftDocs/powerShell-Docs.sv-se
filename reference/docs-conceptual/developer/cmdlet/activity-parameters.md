---
title: Aktivitets parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355673"
---
# <a name="activity-parameters"></a>Aktivitetsparametrar

I följande tabell visas de rekommenderade namnen och funktionerna för aktivitets parametrarna.

|Parameter|Funktioner|
|---|---|
|**Slå**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren kan lägga till innehåll i slutet av en resurs när parametern anges.|
|**CaseSensitive**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren kan kräva Skift läges känslighet när parametern anges.|
|**Kommandoprompt**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en kommando sträng som ska köras.|
|**CompatibleVersion**<br>Datatyp: system. version-objekt|Implementera den här parametern så att användaren kan ange semantiken som cmdleten måste vara kompatibel med för kompatibilitet med tidigare versioner.|
|**Compress**<br>Datatyp: SwitchParameter|Implementera den här parametern så att data komprimering används när parametern anges.|
|**Compress**<br>Datatyp: nyckelord|Implementera den här parametern så att användaren kan ange vilken algoritm som ska användas för data komprimering.|
|**Ständig**<br>Datatyp: SwitchParameter|Implementera den här parametern så att data bearbetas tills användaren avslutar cmdleten när parametern anges. Om parametern inte anges, bearbetar cmdleten en fördefinierad mängd data och avslutar sedan åtgärden.|
|**Fram**<br>Datatyp: SwitchParameter|Implementera den här parametern för att ange att en resurs skapas om en sådan inte redan finns när parametern har angetts.|
|**Ta bort**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resurserna tas bort när cmdleten har slutfört åtgärden när parametern anges.|
|**Flykt**<br>Datatyp: SwitchParameter|Implementera den här parametern för att ange att utestående arbets objekt bearbetas innan cmdleten bearbetar nya data när parametern anges. Om parametern inte anges bearbetas arbets objekt direkt.|
|**Radera**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange hur många gånger en resurs raderas innan den tas bort.|
|**Nivå**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange fel nivå för rapporten.|
|**Ingå**<br>Datatyp: sträng []|Implementera den här parametern så att användaren kan utesluta något från en aktivitet. Mer information om hur du använder inkommande filter finns i [Parametrar för indatafiler](input-filter-parameters.md).|
|**Synkroniseringsfilter**<br>Datatyp: nyckelord|Implementera den här parametern så att användaren kan ange ett filter som väljer vilka resurser som cmdlet-åtgärden ska utföras på. Mer information om hur du använder inkommande filter finns i [Parametrar för indatafiler](./input-filter-parameters.md).|
|**Följt**<br>Datatyp: SwitchParameter|Implementera den här parametern så att förlopp spåras när parametern anges.|
|**Inför**<br>Datatyp: SwitchParameter|Implementera den här parametern för att ange att användaren kan utföra en åtgärd även om begränsningar påträffas när parametern anges. Parametern tillåter inte att säkerhet komprometteras. Med den här parametern kan en användare till exempel skriva över en skrivskyddad fil.|
|**Omfattar**<br>Datatyp: sträng []|Implementera den här parametern så att användaren kan inkludera något i en aktivitet. Mer information om hur du använder inkommande filter finns i [Parametrar för indatafiler](input-filter-parameters.md).|
|**Inkrementell**<br>Datatyp: SwitchParameter|Implementera den här parametern för att ange att bearbetningen utförs stegvis när parametern anges. Med den här parametern kan en användare exempelvis utföra stegvisa säkerhets kopieringar som bara säkerhetskopierar filer sedan den senaste säkerhets kopieringen.|
|**InputObject**<br>Datatyp: objekt|Implementera den här parametern när cmdleten tar emot information från andra cmdletar. När du definierar en **InputObject** -parameter ska du alltid ange nyckelordet **ValueFromPipeline** när du deklarerar attributet **parameter** . Mer information om att använda inkommande filter finns i [Parametrar för indatafiler](./input-filter-parameters.md).|
|**Matning**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten infogar ett objekt när parametern anges.|
|**Ej**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten fungerar interaktivt med användaren när parametern anges.|
|**Intervall**<br>Datatyp: hash-värde|Implementera den här parametern så att användaren kan ange en hash-tabell med nyckelord som innehåller värdena. I följande exempel visas exempel värden för parametern **Interval** : `-interval @{ResumeScan=15; Retry=3}`.|
|**Kvorumloggen**<br>Datatyp: SwitchParameter|Implementera den här parametern granska åtgärdens åtgärder för cmdleten när parametern anges.|
|**NoClobber**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resursen inte kommer att skrivas över när parametern anges. Den här parametern gäller vanligt vis för cmdletar som skapar nya objekt så att de kan förhindras från att skriva över befintliga objekt med samma namn.|
|**Varandra**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren får ett meddelande om att aktiviteten är slutförd när parametern anges.|
|**NotifyAddress**<br>Datatyp: e-postadress|Implementera den här parametern så att användaren kan ange den e-postadress som ska användas för att skicka ett meddelande när en **meddela** -parameter har angetts.|
|**Skriva över**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten skriver över alla befintliga data när parametern anges.|
|**Visas**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en prompt för cmdleten.|
|**Tyst**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten förhindrar användarens feedback under sina åtgärder när parametern anges.|
|**Rekursivt**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdlet: en rekursivt utför sina åtgärder på resurser när parametern anges.|
|**Hjälp**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten försöker korrigera något från ett brutet tillstånd när parametern anges.|
|**RepairString**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en sträng som ska användas när **reparations** parametern anges.|
|**Försök igen**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange hur många gånger cmdleten ska försöka utföra en åtgärd.|
|**Select**<br>Datatyp: nyckelords mat ris|Implementera den här parametern så att användaren kan ange en matris av olika typer av objekt.|
|**Skicka**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren kan strömma flera utgående objekt via pipelinen när parametern har angetts.|
|**Begränsade**<br>Datatyp: SwitchParameter|Implementera den här parametern så att alla fel hanteras som avslutande fel när parametern anges.|
|**TempLocation**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange platsen för tillfälliga data som används under cmdlet-cmdlet-åtgärden.|
|**Standardvärde**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange timeout-intervall (i millisekunder).|
|**Trunkera**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten kommer att trunkera sina åtgärder när parametern anges. Om parametern inte anges utför cmdleten en annan åtgärd.|
|**Kontrollen**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten kommer att testa för att avgöra om en åtgärd har inträffat när parametern anges.|
|**Vänta**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten väntar på användarindata innan du fortsätter när parametern anges.
|**Vänte tid**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange den varaktighet (i sekunder) som cmdleten ska vänta på användarindata när **wait** -parametern anges.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
