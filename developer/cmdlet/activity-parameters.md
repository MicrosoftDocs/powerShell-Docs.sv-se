---
title: Parametrarna för aktiviteten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075196"
---
# <a name="activity-parameters"></a>Parametrarna för aktiviteten

I följande tabell visas de rekommenderade namn och de funktioner för parametrarna för aktiviteten.

|Parameter|Funktioner|
|---|---|
|**Lägg till**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren kan lägga till innehåll i slutet av en resurs när parametern har angetts.|
|**CaseSensitive**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren kan kräva skiftlägeskänslighet när parametern har angetts.|
|**Kommandot**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en kommandosträng ska köras.|
|**CompatibleVersion**<br>Datatyp: System.Version object|Implementera den här parametern så att användaren kan ange semantik som cmdlet: en måste vara kompatibel med för kompatibilitet med tidigare versioner.|
|**Komprimera**<br>Datatyp: SwitchParameter|Implementera den här parametern så att datakomprimering används när parametern anges.|
|**Komprimera**<br>Datatyp: Nyckelord|Implementera den här parametern så att användaren kan ange algoritmen som ska användas för komprimering.|
|**Kontinuerlig**<br>Datatyp: SwitchParameter|Implementera den här parametern så att data har bearbetats tills användaren avslutar cmdleten när parametern har angetts. Om parametern inte anges, cmdleten bearbetar en fördefinierad mängd data och avbryter åtgärden.|
|**Skapa**<br>Datatyp: SwitchParameter|Implementera den här parametern om du vill ange att en resurs skapas om det inte redan finns när parametern har angetts.|
|**Ta bort**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resurser tas bort när cmdleten har slutförts åtgärden när parametern har angetts.|
|**Töm**<br>Datatyp: SwitchParameter|Implementera den här parametern om du vill ange att återstående arbetsuppgifter bearbetas innan cmdleten bearbetar nya data när parametern anges. Om parametern inte anges, behandlas arbetsobjekt direkt.|
|**Radera**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange hur många gånger som en resurs tas bort innan de tas bort.|
|**errorLevel**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange nivån av fel till rapporten.|
|**Exkludera**<br>Datatyp: String[]|Implementera den här parametern så att användaren kan utesluta något från en aktivitet. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](input-filter-parameters.md).|
|**Filter**<br>Datatyp: Nyckelord|Implementera den här parametern så att användaren kan ange ett filter som väljs de resurser som du vill utföra cmdlet-åtgärden. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).|
|**Följ**<br>Datatyp: SwitchParameter|Implementera den här parametern så att förloppet spåras när parametern har angetts.|
|**Force**<br>Datatyp: SwitchParameter|Implementera den här parametern för att ange att användaren kan utföra en åtgärd även om begränsningar uppstår när parametern har angetts. Parametern tillåter inte att säkerheten äventyras. Den här parametern kan till exempel en användare skriver över en skrivskyddad fil.|
|**Inkludera**<br>Datatyp: String[]|Implementera den här parametern så att användaren kan innehålla något i en aktivitet. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](input-filter-parameters.md).|
|**Inkrementell**<br>Datatyp: SwitchParameter|Implementera den här parametern om du vill ange att bearbetning utförs stegvis när parametern har angetts. Den här parametern kan till exempel en användare att utföra inkrementella säkerhetskopieringar som säkerhetskopierar filer endast sedan den senaste säkerhetskopieringen.|
|**InputObject**<br>Datatyp: Object|Implementera den här parametern när cmdlet: en hämtar indata från andra cmdletar. När du definierar en **InputObject** parametern alltid ange den **ValueFromPipeline** nyckelord när du deklarerar den **parametern** attribut. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).|
|**Infoga**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten infogar ett objekt när parametern har angetts.|
|**Interaktiv**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten fungerar interaktivt med användaren när parametern anges.|
|**intervall**<br>Datatyp: Hash-tabell|Implementera den här parametern så att användaren kan ange en hash-tabell över nyckelord som innehåller värdena. I följande exempel visar exempelvärden för den **intervall** parameter: `-interval @{ResumeScan=15; Retry=3}`.|
|**log**<br>Datatyp: SwitchParameter|Implementera den här parametern granskning av cmdlet: en när parametern har angetts.|
|**NoClobber**<br>Datatyp: SwitchParameter|Implementera den här parametern så att resursen inte ska skrivas över när parametern anges. Den här parametern gäller vanligtvis för cmdletar som skapar nya objekt så att de kan förhindras från att skriva över befintliga objekt med samma namn.|
|**Meddela**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren ska meddelas att aktiviteten har slutförts när parametern har angetts.|
|**NotifyAddress**<br>Datatyp: E-postadress|Implementera den här parametern så att användaren kan ange den e-postadressen du använder för att skicka ett meddelande när den **meddela** parameter har angetts.|
|**Skriv över**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten skriver över befintliga data när parametern har angetts.|
|**fråga**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en prompt som ber cmdleten.|
|**tyst**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten Undertrycker Användarfeedback under dess åtgärder när parametern har angetts.|
|**Recurse**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdlet-rekursivt utför dess åtgärder på resurser när parametern anges.|
|**Reparation**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten ska försöka korrigera något från skadas när parametern har angetts.|
|**RepairString**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en sträng som ska användas när den **reparera** parameter har angetts.|
|**Försök igen**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange hur många gånger som cmdleten försöker en åtgärd.|
|**Välj**<br>Datatyp: Nyckelordet matris|Implementera den här parametern så att användaren kan ange en matris med vilka typer av objekt.|
|**Stream**<br>Datatyp: SwitchParameter|Implementera den här parametern så att användaren kan strömma flera utdata objekt genom pipelinen när parametern har angetts.|
|**Strikt**<br>Datatyp: SwitchParameter|Implementera den här parametern så att alla fel hanteras som avslutande fel när parametern har angetts.|
|**TempLocation**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange platsen för tillfälliga data som används under driften av cmdlet: en.|
|**Timeout**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange timeout-intervall (i millisekunder).|
|**Trunkera**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten trunkerar dess åtgärder när parametern har angetts. Om parametern inte anges, utför cmdlet: en annan åtgärd.|
|**Kontrollera**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten kommer att testa för att avgöra om en åtgärd har uppstått när parametern har angetts.|
|**Vänta**<br>Datatyp: SwitchParameter|Implementera den här parametern så att cmdleten väntar på indata från användaren innan du fortsätter när parametern har angetts.
|**WaitTime**<br>Datatyp: Int32|Implementera den här parametern så att användaren kan ange varaktighet (i sekunder) att cmdleten ska vänta tills användaren ange när den **vänta** parameter har angetts.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
