---
title: Godkända verb för PowerShell-kommandon | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068750"
---
# <a name="approved-verbs-for-powershell-commands"></a>Godkända verb för PowerShell-kommandon

PowerShell använder ett verb-substantiv-par för namnen på cmdletar och deras härledda klasser för Microsoft .NET Framework.
Till exempel den `Get-Command` cmdlet som tillhandahålls av PowerShell används för att ta emot de kommandon som är registrerade i PowerShell.
Verb del av namnet identifierar den åtgärd som utförs av cmdlet: en.
Substantiv-del av namnet identifierar den entitet som åtgärden utförs.

> [!NOTE]
> PowerShell använder termen *verb* att beskriva ett ord som antyder en åtgärd, även om ordet inte är ett verb som standard på engelska.
> Till exempel termen *New* är ett giltigt namn för PowerShell-verb eftersom en åtgärd innebär även om det inte är ett verb på engelska.

## <a name="verb-naming-rules"></a>Reglerna för namngivning av verb

Följande lista innehåller riktlinjer för att tänka på när du väljer verb för en cmdlet-namn:

* När du anger verbet, rekommenderar vi att du använder något av de fördefinierade verb som tillhandahålls av PowerShell (alias för dessa fördefinierade verb som ingår i tabellerna nedan).
  När du använder ett fördefinierat verb, kontrollera konsekvensen mellan de cmdletar som du skapar och de cmdletar som tillhandahålls av PowerShell cmdlets som utformats av andra.

* Använda fördefinierade verb som beskriver allmänna omfånget för åtgärden och använda parametrar för att ytterligare förfina åtgärden av cmdlet: en.

* Om du vill framtvinga konsekvens i cmdletar, Använd inte en synonym för ett godkänt verb.

* Använd endast form av varje verb som anges i det här avsnittet.
  Till exempel använda ”Get”, men Använd inte ”hämta” eller ”hämtar”.

* Använda Pascal skiftläge för verb.
  I Pascal skiftläge den första bokstaven i varje ord blir en versal, till exempel ”ForEach”.

* Använd inte följande reserverade verb eller alias.
  Dessa verb som används av PowerShell-språket eller genom att särskilda fall cmdletar som tillhandahålls i PowerShell.
  - ForEach (foreach)
  - Format (f)
  - Grupp (gp)
  - Sortera (sr)
  - Tee (te)
  - Där (n)

## <a name="similar-verbs-for-different-actions"></a>Liknande verb för olika åtgärder

Följande liknande verb representerar olika åtgärder.

### <a name="new-vs-set"></a>Ny vs. Ange
Den `New` verb som används för att skapa en ny resurs.
Den `Set` verb som används för att ändra en befintlig resurs om du vill skapa en resurs om det inte finns, till exempel den `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Hitta vs. Search
Den `Find` verb som används för att leta efter ett objekt.
Den `Search` verb som används för att skapa en referens till en resurs i en behållare.

### <a name="get-vs-read"></a>Hämta vs. Läsa
Den `Get` verb som används för att hämta en resurs, till exempel en fil.
Den `Read` verb som används för att hämta information från en källa, till exempel en fil.

### <a name="invoke-vs-start"></a>Anropa vs. Starta
Den `Invoke` verb som används för att utföra en åtgärd som är vanligtvis en synkron åtgärd, t.ex köra ett kommando.
Den `Start` verb som används för att starta en åtgärd som är vanligtvis en asynkron åtgärd, till exempel starta en process.

### <a name="ping-vs-test"></a>Jämfört med ping Testa
Använd den `Test` verb.

## <a name="common-verbs"></a>Vanliga verb

PowerShell använder den [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) uppräkningsklassen för att definiera allmänna åtgärder som kan använda för nästan alla cmdlet.
I följande tabell visas de flesta av de definierade verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Lägg till](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Lägger till en resurs till en behållare eller bifogar ett objekt till ett annat objekt. Till exempel den `Add-Content` cmdlet lägger till innehåll till en fil. Den här verb paras ihop med `Remove`.|För den här åtgärden att inte använda verb, till exempel lägga till, Attach, sammanfoga eller genom att infoga.|
|[Rensa](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Tar bort alla resurser från en behållare, men ta bort inte behållaren. Till exempel den `Clear-Content` cmdlet tar bort innehållet i en fil, men inte ta bort filen.|Använd inte verb, till exempel tömning, radera, version, avmarkera, inaktivera eller Nullify den här åtgärden.|
|[Stäng](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Ändrar tillståndet för en resurs så att de blir otillgänglig, inte tillgänglig eller inte kan användas. Den här verb paras ihop med `Open.`||
|[Kopiera](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Kopierar en resurs till ett annat namn eller till en annan behållare. Till exempel den `Copy-Item` cmdlet som används för att få åtkomst till lagrade data kopierar ett objekt från en plats i datalagret till en annan plats.|Använd inte verb som dubblett, klona, replikering eller synkronisering av den här åtgärden.|
|[Ange](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (svensk tid)|Anger en åtgärd som används att flytta till en resurs. Till exempel den `Enter-PSSession` cmdlet placerar användaren i en interaktiv session. Den här verb paras ihop med `Exit`.|Använd inte verb, till exempel Push eller i den här åtgärden.|
|[Avsluta](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Anger den aktuella miljön eller kontext till senast använda kontexten. Till exempel den `Exit-PSSession` cmdlet placerar användaren i sessionen som användes för att starta den interaktiva sessionen. Den här verb paras ihop med `Enter`.|Använd inte verb, till exempel Pop eller ut den här åtgärden.|
|[Hitta](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Söker efter ett objekt i en behållare som är okänd, UNDERFÖRSTÅDDA, valfri eller angivna.||
|[Formatet](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Ordnar objekt i en specificerad form eller layout.||
|[Hämta](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Anger en åtgärd som hämtar en resurs. Den här verb paras ihop med `Set`.|Använd inte verb, till exempel läsa, öppna, Cat, typ, Dir, hämta, Dump, hämta, granska, Sök eller Sök den här åtgärden.|
|[Dölj](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Gör en resurs oidentifierbart. Till exempel döljer en cmdlet vars namn innehåller Dölj verbet en tjänst från en användare. Den här verb paras ihop med `Show`.|Använd inte ett verb, till exempel blockera den här åtgärden.|
|[Ansluta till](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Kombinerar resurser till en resurs. Till exempel den `Join-Path` cmdlet kombinerar en sökväg med någon av dess underordnade sökvägar för att skapa en enskild sökväg. Den här verb paras ihop med `Split`.|Använd inte verb, till exempel kombinera, Unite, Anslut eller koppla den här åtgärden.|
|[Lås](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Skyddar en resurs. Den här verb paras ihop med `Unlock`.|Använd inte verb, till exempel begränsa eller Secure den här åtgärden.|
|[Flytta](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Flyttar en resurs från en plats till en annan. Till exempel den `Move-Item` cmdlet flyttar ett objekt från en plats i datalagret till en annan plats.|Använd inte verb, till exempel överföring, namn eller migrera den här åtgärden.|
|[Ny](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Skapar en resurs. (Den `Set` verb kan också användas när du skapar en resurs som innehåller data, t.ex. den `Set-Variable` cmdlet: en.)|Använd inte verb, till exempel skapa, generera, Build, kontrollera eller tilldela den här åtgärden.|
|[Öppna](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Ändrar tillståndet för en resurs så att de blir tillgängliga, tillgängliga eller kan användas. Den här verb paras ihop med `Close`.||
|[Optimera](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Ökar effektiviteten i en resurs.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Tar bort ett objekt från toppen av en samling. Till exempel den `Pop-Location` cmdlet ändrar den aktuella platsen till den plats som nyligen pushades till stacken.||
|[Push-](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Lägger till ett objekt i toppen av en samling. Till exempel den `Push-Location` cmdleten skickar den aktuella platsen till stacken.||
|[Gör om](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (åter)|Återställer en resurs till det tillstånd som har ångrats.||
|[Ta bort](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Tar bort en resurs från en behållare. Till exempel den `Remove-Variable` cmdlet tar bort en variabel och dess värde. Den här verb paras ihop med `Add`.|För den här åtgärden inte använda verb sådana som klartext, Klipp ut, ta bort borttagna objekt, eller radera.|
|[Byt namn på](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Ändrar namnet på en resurs. Till exempel den `Rename-Item` cmdlet, som används för att få åtkomst till lagrade data, som ändrar namnet på ett objekt i datalagret.|Använd inte ett verb, till exempel ändra den här åtgärden.|
|[Återställ](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Anger en resurs till dess ursprungliga tillstånd.||
|[Sök](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Skapar en referens till en resurs i en behållare.|Använd inte verb, till exempel Sök eller hitta den här åtgärden.|
|[Välj](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Söker efter en resurs i en behållare. Till exempel den `Select-String` cmdleten söker efter text i strängar och filer.|Använd inte verb, till exempel Sök eller hitta den här åtgärden.|
|[Ange](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Ersätter data på en befintlig resurs eller skapar en resurs som innehåller vissa data. Till exempel den `Set-Date` cmdlet ändrar systemklockan på den lokala datorn. (Den `New` verb kan också användas för att skapa en resurs.) Den här verb paras ihop med `Get`.|Använd inte verb, till exempel skriva, återställning, tilldela eller konfigurera den här åtgärden.|
|[Visa](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Gör en resurs som är synliga för användaren. Den här verb paras ihop med `Hide`.|Använd inte verb, till exempel visa eller skapa den här åtgärden.|
|[Hoppa över](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Kringgår en eller flera resurser eller punkter i en sekvens.|Använd inte ett verb, till exempel kringgå eller ett hopp den här åtgärden.|
|[Dela](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Separerar delar av en resurs. Till exempel den `Split-Path` cmdlet returnerar olika delar av en sökväg. Den här verb paras ihop med `Join`.|För den här åtgärden inte Använd ett verb sådana separat.|
|[Steg](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Flyttar till nästa punkt eller resurs i en sekvens.||
|[Växeln](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Anger en åtgärd som växlar mellan två resurser, till exempel ändra mellan två platser, ansvarsområden eller tillstånd.||
|[Ångra](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (o)|Anger en resurs till sitt tidigare tillstånd.||
|[Låsa upp](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Storbritannien)|Frigör en resurs som har låsts. Den här verb paras ihop med `Lock`.|Du inte använda verb, till exempel versionen, Unrestrict eller ta bort skydd för den här åtgärden.|
|[Titta på](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Kontinuerligt inspekterar eller övervakar en resurs för ändringar.||

## <a name="communications-verbs"></a>Kommunikation verb

PowerShell använder den [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) klassen för att definiera åtgärder som gäller för kommunikation.
I följande tabell visas de flesta av de definierade verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Ansluta](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (kopia)|Skapar en länk mellan en källa och ett mål. Den här verb paras ihop med `Disconnect`.|Använd inte verb, till exempel kopplings- eller Telnet den här åtgärden.|
|[Koppla från](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Delar länken mellan en källa och ett mål. Den här verb paras ihop med `Connect`.|Använd inte verb, till exempel Break eller logga ut den här åtgärden.|
|[Läs](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Hämtar information från en källa. Den här verb paras ihop med `Write`.|För den här åtgärden att inte använda verb, till exempel hämta kommandoprompt eller genom att hämta.|
|[Ta emot](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Accepterar informationen som skickas från en källa. Den här verb paras ihop med `Send`.|För den här åtgärden inte använda verb, till exempel läsa, acceptera, och granska.|
|[Skicka](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (DV)|Skickar information till ett mål. Den här verb paras ihop med `Receive`.|Använd inte verb, till exempel placera, sändning, e-post eller Fax den här åtgärden.|
|[Skriva](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Lägger till information till ett mål. Den här verb paras ihop med `Read`.|Använd inte verb, till exempel placera eller Skriv ut den här åtgärden.|

## <a name="data-verbs"></a>Data verb

PowerShell använder den [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) klassen för att definiera åtgärder som gäller för datahantering.
I följande tabell visas de flesta av de definierade verb.

|Verb namn (alias)|Åtgärd|Kommentar|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Lagrar data genom att replikera den.|Använd inte verb som Spara bränna, replikering eller synkronisering den här åtgärden.|
|[Kontrollpunkt](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Skapar en ögonblicksbild av det aktuella tillståndet för data eller dess konfiguration.|För den här åtgärden inte Använd ett verb, till exempel skillnad|
|[Jämför](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Utvärderar data från en resurs med data från en annan resurs.|För den här åtgärden inte Använd ett verb, till exempel skillnad|
|[Komprimera](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Komprimerar data för en resurs. Kan användas med `Expand`.|För den här åtgärden att inte använda ett verb, till exempel CD.|
|[Konvertera](/dotnet/api/System.Management.Automation.VerbsData.Convert) (KA)|Ändrar data från en representation till en annan när cmdleten stöder dubbelriktade konvertering eller när cmdleten har stöd för konvertering mellan olika datatyper.|För den här åtgärden inte använda verb, till exempel ändra, ändra storlek på, eller sampla om.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Konverterar en primära typ av indata (cmdlet-substantiv anger indata) till en eller flera typer av stöds utdata.|Använd inte verb, till exempel Export eller utdata ut den här åtgärden.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Konverterar från en eller flera typer av indata för en primär utdatatypen (cmdlet-substantiv anger utdatatypen).|För den här åtgärden inte använder verb, till exempel Import, mata in, eller i.|
|[Demontera](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Kopplar från en namngiven entitet från en plats. Den här verb paras ihop med `Mount`.|Använd inte verb, till exempel demonteringen till eller Avlänka från den här åtgärden.|
|[Redigera](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Ändrar befintliga data genom att lägga till eller ta bort innehåll.|Använd inte verb, till exempel ändra, uppdatera eller ändra den här åtgärden.|
|[Expandera](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Återställer data för en resurs som har komprimerats till det ursprungliga tillståndet. Den här verb paras ihop med `Compress`.|Använd inte verb, till exempel explosion eller expandera den här åtgärden.|
|[Exportera](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Kapslar in primära indata till ett beständigt datalager, till exempel en fil eller till ett utbytesformat. Den här verb paras ihop med `Import`.|För den här åtgärden att inte använda verb, till exempel extrahering eller säkerhetskopiering.|
|[Gruppen](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Ordnar eller kopplar en eller flera resurser.|För den här åtgärden att inte använda verb, till exempel aggregering, ordna, koppla eller genom att korrelera.|
|[Importera](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Skapar en resurs från data som lagras i ett beständigt datalager (till exempel en fil) eller i ett utbytesformat. Till exempel den `Import-CSV` cmdlet: en importerar data från en fil med kommaavgränsade värden (CSV) för objekt som kan användas av andra cmdlet: ar. Den här verb paras ihop med `Export`.|Använd inte verb, till exempel BulkLoad eller läsa in den här åtgärden.|
|[Initiera](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (i)|Förbereder en resurs för användning och ställer in den på ett standardtillstånd.|Använd inte verb, till exempel radera Init, förnya, återskapa, initiera eller installationen den här åtgärden.|
|[Gränsen](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Gäller begränsningar för en resurs.|Du inte använda ett verb, till exempel kvot för den här åtgärden.|
|[Sammanfoga](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Skapar en enskild resurs från flera resurser.|Använd inte verb, till exempel kombinera eller Anslut till den här åtgärden.|
|[Montera](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Bifogar en namngiven entitet till en plats. Den här verb paras ihop med `Dismount`.|Använd inte verb Anslut den här åtgärden.|
|[Ut](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Skickar data från miljön. Till exempel den `Out-Printer` cmdleten skickar data till en skrivare.||
|[Publicera](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Gör en resurs som är tillgänglig för andra. Den här verb paras ihop med `Unpublish`.|För den här åtgärden inte använda verb, till exempel distribuera, versionen och installera.|
|[Återställa](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Anger en resurs till en fördefinierad tillstånd, till exempel ett tillstånd som anges av `Checkpoint`. Till exempel den `Restore-Computer` cmdlet startar en återställning på den lokala datorn.|Använd inte verb, till exempel reparation, returnera, ångra eller åtgärda den här åtgärden.|
|[Spara](/dotnet/api/System.Management.Automation.VerbsData.Save) (SA)|Bevarar data för att undvika dataförlust.||
|[Synkronisera](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Säkerställer att det finns två eller flera resurser i samma tillstånd.|För den här åtgärden inte använda verb, till exempel replikera Coerce, eller matcha.|
|[Ta bort](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Gör en resurs inte är tillgänglig för andra. Den här verb paras ihop med `Publish`.|För den här åtgärden inte använda verb, till exempel avinstallera, återställning, eller dölja.|
|[Uppdatera](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Ger en resurs som är uppdaterade att upprätthålla dess tillstånd, korrekthet, efterlevnadsstatus eller efterlevnad. Till exempel den `Update-FormatData` cmdlet uppdaterar och lägger till formatering filer i den aktuella PowerShell-konsolen.|För den här åtgärden att inte använda verb, till exempel beräkna om uppdatering, förnya, eller genom att indexera.|

## <a name="diagnostic-verbs"></a>Diagnostiska verb

PowerShell använder den [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) klassen för att definiera åtgärder som gäller för diagnostik.
I följande tabell visas de flesta av de definierade verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Felsöka](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Undersöker en resurs för att diagnostisera Driftproblem.|Använd inte ett verb, till exempel diagnostisera den här åtgärden.|
|[Måttet](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifiera resurser som förbrukas av en specificerad åtgärd eller hämtar statistik om en resurs.|Använd inte verb, till exempel beräkna, ta reda på och analysera den här åtgärden.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Använd den `Test` verb.||
|[Reparera](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Återställer en resurs till ett villkor som kan användas|Använd inte verb, till exempel korrigera eller återställa den här åtgärden.|
|[Lösa](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Mappar en snabbformat representation av en resurs till en mer fullständig återgivning.|Använd inte verb, till exempel expandera eller ta reda på den här åtgärden.|
|[Testa](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Kontrollerar igen eller konsekvenskontroll av en resurs.|Använd inte verb, till exempel identifiera, analysera, restvärde eller verifiera den här åtgärden.|
|[Spårningen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Spårar aktiviteter för en resurs.|För den här åtgärden att inte använda verb, till exempel spåra, följ, granska eller genom att gå på.|

## <a name="lifecycle-verbs"></a>Livscykel verb

PowerShell använder den [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klassen för att definiera åtgärder som gäller för livscykeln för en resurs.
I följande tabell visas de flesta av de definierade verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Godkänn](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Bekräftar eller samtycker till att statusen för en resurs eller process.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (som)|Bekräftas tillståndet för en resurs.|Använd inte ett verb, till exempel certifiera den här åtgärden.|
|[Skapa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Skapar en artefakt (vanligtvis en binär fil eller dokumentet) utanför vissa uppsättning indatafilerna (vanligtvis källkoden eller deklarativa dokument)|Den här verb har lagts till i PowerShell v6|
|[Fullständig](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Avslutar en åtgärd.||
|[Bekräfta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Bekräftar, verifierar eller verifierar tillståndet för en resurs eller process.|Använd inte verb, till exempel bekräfta, accepterar, Certify, verifiera eller verifiera den här åtgärden.|
|[Neka](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Vägrar, objekt, blockerar eller motsätter sig tillståndet för en resurs eller process.|För den här åtgärden att inte använda verb, till exempel Block, objekt, vägra eller genom att avvisa.|
|[Distribuera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Skickar ett program, en webbplats eller en lösning till en fjärransluten mål [s] så att konsumenter av lösningen kan komma åt den när distributionen är klar|Den här verb har lagts till i PowerShell v6|
|[Inaktivera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Konfigurerar en resurs till en otillgänglig eller inaktiv status. Till exempel den `Disable-PSBreakpoint` cmdlet gör en brytpunkt som är inaktiva. Den här verb paras ihop med `Enable`.|Använd inte verb, till exempel uppehåll eller Dölj den här åtgärden.|
|[Aktivera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Konfigurerar en resurs till en tillgänglig eller aktivt tillstånd. Till exempel den `Enable-PSBreakpoint` cmdlet gör en brytpunkt active. Den här verb paras ihop med `Disable`.|Använd inte verb, till exempel starta eller börjar den här åtgärden.|
|[Installera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (är)|Placerar en resurs på en plats och du kan också initierar den. Den här verb paras ihop med `Uninstall`.|Gör inte ett Använd verb, till exempel installationsprogrammet för den här åtgärden.|
|[Anropa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Utför en åtgärd, som kör ett kommando eller en metod.|Använd inte verb, till exempel kör eller starta den här åtgärden.|
|[Registrera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Skapar en post för en resurs i en lagringsplats, till exempel en databas. Den här verb paras ihop med `Unregister`.||
|[Begär](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Begär en resurs eller begär behörigheter.||
|[Starta om](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Stoppar en åtgärd och sedan startar det igen. Till exempel den `Restart-Service` cmdlet stoppar och startar en tjänst.|Använd inte ett verb, till exempel omarbetning av den här åtgärden.|
|[Återuppta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Startar en åtgärd som har pausats. Till exempel den `Resume-Service` cmdlet startar en tjänst som har pausats. Den här verb paras ihop med `Suspend`.||
|[Starta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Initierar en åtgärd. Till exempel den `Start-Service` cmdlet startar en tjänst. Den här verb paras ihop med `Stop`.|Använd inte verb, till exempel starta eller initiera start den här åtgärden.|
|[Stoppa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Upphör en aktivitet. Den här verb paras ihop med `Start`.|För den här åtgärden inte använda verb, till exempel slutet, Kill, avsluta, eller Avbryt.|
|[Skicka](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Anger en resurs för godkännande.|Använd inte ett verb, till exempel efter den här åtgärden.|
|[Pausa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Pausar en aktivitet. Till exempel den `Suspend-Service` cmdlet pausar en tjänst. Den här verb paras ihop med `Resume`.|Använd inte ett verb, till exempel Pausa den här åtgärden.|
|[Avinstallera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (USA)|Tar bort en resurs från en angiven plats. Den här verb paras ihop med `Install`.||
|[Avregistrera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (dina)|Tar bort posten för en resurs från en databas. Den här verb paras ihop med `Register`.|Använd inte ett verb, till exempel ta bort den här åtgärden.|
|[Vänta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Pausar en åtgärd tills ett angivna händelsen inträffar. Till exempel den `Wait-Job` cmdlet pausar åtgärder förrän en eller flera av bakgrundsjobb är klar.|Använd inte verb, till exempel viloläge eller pausa den här åtgärden.|

## <a name="security-verbs"></a>Security verb

PowerShell använder den [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) klassen för att definiera åtgärder som gäller för säkerhet.
I följande tabell visas de flesta av de definierade verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Blockera](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Begränsar åtkomsten till en resurs. Den här verb paras ihop med `Unblock`.|Använd inte verb, till exempel förhindra eller begränsa neka den här åtgärden.|
|[Bevilja](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Ger åtkomst till en resurs. Den här verb paras ihop med `Revoke`.|Använd inte verb, till exempel tillåta eller aktivera den här åtgärden.|
|[Skydda](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Skyddar en resurs från angrepp eller förlust. Den här verb paras ihop med `Unprotect`.|Använd inte verb, till exempel kryptera eller skydda försegla den här åtgärden.|
|[Återkalla](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rksskrivare)|Anger en åtgärd som inte tillåter åtkomst till en resurs. Den här verb paras ihop med `Grant`.|Använd inte verb, till exempel ta bort eller inaktivera den här åtgärden.|
|[Avblockera](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Tar bort begränsningar för en resurs. Den här verb paras ihop med `Block`.|Använd inte verb, till exempel Clear eller Tillåt den här åtgärden.|
|[Ta bort skyddet från](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (upp)|Tar bort skydd från en resurs som har lagts till att förhindra att den attack eller förlust. Den här verb paras ihop med `Protect`.|Använd inte verb, till exempel dekryptering eller Unseal den här åtgärden.|

## <a name="other-verbs"></a>Övriga verb

PowerShell använder den [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) klassen för att definiera canonical verb-namn som inte passar i ett visst verb namn kategori som vanligt, kommunikation, data, livscykel eller säkerhet verb namn verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Använd](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Använder eller innehåller en resurs för att göra något.||

## <a name="see-also"></a>Se även

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet: en deklaration](./cmdlet-class-declaration.md)

[Programmeringsguide för Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
