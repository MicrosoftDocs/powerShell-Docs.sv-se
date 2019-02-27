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
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849093"
---
# <a name="activity-parameters"></a>Aktivitetsparametrar

I följande tabell visas de rekommenderade namn och de funktioner för parametrarna för aktiviteten.

Lägg till datatypen: SwitchParameter

Implementera den här parametern så att användaren kan lägga till innehåll i slutet av en resurs när parametern har angetts.

CaseSensitive datatyp: SwitchParameter

Implementera den här parametern så att användaren kan kräva skiftlägeskänslighet när parametern har angetts.

Kommandot datatyp: Sträng

Implementera den här parametern så att användaren kan ange en kommandosträng ska köras.

CompatibleVersion datatyp: System.Version object

Implementera den här parametern så att användaren kan ange semantik som cmdlet: en måste vara kompatibel med för kompatibilitet med tidigare versioner.

Komprimera datatyp: SwitchParameter

Implementera den här parametern så att datakomprimering används när parametern anges.

Komprimera datatyp: Nyckelord

Implementera den här parametern så att användaren kan ange algoritmen som ska användas för komprimering.

Kontinuerlig datatyp: SwitchParameter

Implementera den här parametern så att data har bearbetats tills användaren avslutar cmdleten när parametern har angetts. Om parametern inte anges, cmdleten bearbetar en fördefinierad mängd data och avbryter åtgärden.

Skapa datatyp: SwitchParameter

Implementera den här parametern om du vill ange att en resurs skapas om det inte redan finns när parametern har angetts.

Ta bort datatypen: SwitchParameter

Implementera den här parametern så att resurser tas bort när cmdleten har slutförts åtgärden när parametern har angetts.

Tömma datatyp: SwitchParameter

Implementera den här parametern om du vill ange att återstående arbetsuppgifter bearbetas innan cmdleten bearbetar nya data när parametern anges. Om parametern inte anges, behandlas arbetsobjekt direkt.

Radera datatyp: Int32

Implementera den här parametern så att användaren kan ange hur många gånger som en resurs tas bort innan de tas bort.

ErrorLevel datatyp: Int32

Implementera den här parametern så att användaren kan ange nivån av fel till rapporten.

Exkludera datatyp: String[]

Implementera den här parametern så att användaren kan utesluta något från en aktivitet. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).

Filtrera datatyp: Nyckelord

Implementera den här parametern så att användaren kan ange ett filter som väljs de resurser som du vill utföra cmdlet-åtgärden. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).

Följ datatyp: SwitchParameter

Implementera den här parametern så att förloppet spåras när parametern har angetts.

Tvinga datatyp: SwitchParameter

Implementera den här parametern för att ange att användaren kan utföra en åtgärd även om begränsningar uppstår när parametern har angetts. Parametern tillåter inte att säkerheten äventyras. Den här parametern kan till exempel en användare skriver över en skrivskyddad fil.

Med datatypen: String[]

Implementera den här parametern så att användaren kan innehålla något i en aktivitet. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).

Inkrementell datatyp: SwitchParameter

Implementera den här parametern om du vill ange att bearbetning utförs stegvis när parametern har angetts. Den här parametern kan till exempel en användare att utföra inkrementella säkerhetskopieringar som säkerhetskopierar filer endast sedan den senaste säkerhetskopieringen.

InputObject datatyp: Objekt

Implementera den här parametern när cmdlet: en hämtar indata från andra cmdletar. När du definierar en `InputObject` parametern alltid ange den `ValueFromPipeline` nyckelord när du deklarerar den **parametern** attribut. Läs mer om hur du använder filter för inkommande trafik, [Filter indataparametrar](./input-filter-parameters.md).

Infoga datatyp: SwitchParameter

Implementera den här parametern så att cmdleten infogar ett objekt när parametern har angetts.

Interaktiv datatyp: SwitchParameter

Implementera den här parametern så att cmdleten fungerar interaktivt med användaren när parametern anges.

Intervalltyp för Data: Hash-tabell

Implementera den här parametern så att användaren kan ange en hash-tabell över nyckelord som innehåller värdena. I följande exempel visar exempelvärden för den `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.

Loggdata skriver du: SwitchParameter

Implementera den här parametern granskning av cmdlet: en när parametern har angetts.

NoClobber datatyp: SwitchParameter

Implementera den här parametern så att resursen inte ska skrivas över när parametern anges. Den här parametern gäller vanligtvis för cmdletar som skapar nya objekt så att de kan förhindras från att skriva över befintliga objekt med samma namn.

Meddela datatyp: SwitchParameter

Implementera den här parametern så att användaren ska meddelas att aktiviteten har slutförts när parametern har angetts.

NotifyAddress datatyp: E-postadress

Implementera den här parametern så att användaren kan ange den e-postadressen du använder för att skicka ett meddelande när den `Notify` parameter har angetts.

Skriv över datatyp: SwitchParameter

Implementera den här parametern så att cmdleten skriver över befintliga data när parametern har angetts.

Fråga datatyp: Sträng

Implementera den här parametern så att användaren kan ange en prompt som ber cmdleten.

Tyst datatyp: SwitchParameter

Implementera den här parametern så att cmdleten Undertrycker Användarfeedback under dess åtgärder när parametern har angetts.

Recurse datatyp: SwitchParameter

Implementera den här parametern så att cmdlet-rekursivt utför dess åtgärder på resurser när parametern anges.

Reparera datatyp: SwitchParameter

Implementera den här parametern så att cmdleten ska försöka korrigera något från skadas när parametern har angetts.

RepairString datatyp: Sträng

Implementera den här parametern så att användaren kan ange en sträng som ska användas när den `Repair` parameter har angetts.

Gör om-datatypen: Int32

Implementera den här parametern så att användaren kan ange hur många gånger som cmdleten försöker en åtgärd.

Välj typ av Data: Nyckelordet matris

Implementera den här parametern så att användaren kan ange en matris med vilka typer av objekt.

Stream-datatyp: SwitchParameter

Implementera den här parametern så att användaren kan strömma flera utdata objekt genom pipelinen när parametern har angetts.

Strikt datatyp: SwitchParameter

Implementera den här parametern så att alla fel hanteras som avslutande fel när parametern har angetts.

TempLocation datatyp: Sträng

Implementera den här parametern så att användaren kan ange platsen för tillfälliga data som används under driften av cmdlet: en.

Tidsgräns för datatyp: Int32

Implementera den här parametern så att användaren kan ange timeout-intervall (i millisekunder).

Trunkera datatyp: SwitchParameter

Implementera den här parametern så att cmdleten trunkerar dess åtgärder när parametern har angetts. Om parametern inte anges, utför cmdlet: en annan åtgärd.

Kontrollera typ av Data: SwitchParameter

Implementera den här parametern så att cmdleten kommer att testa för att avgöra om en åtgärd har uppstått när parametern har angetts.

Vänta datatyp: SwitchParameter

Implementera den här parametern så att cmdleten väntar på indata från användaren innan du fortsätter när parametern har angetts.

Väntetid datatyp: Int32

Implementera den här parametern så att användaren kan ange varaktighet (i sekunder) att cmdleten ska vänta tills användaren ange när den `Wait` parameter har angetts.

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
