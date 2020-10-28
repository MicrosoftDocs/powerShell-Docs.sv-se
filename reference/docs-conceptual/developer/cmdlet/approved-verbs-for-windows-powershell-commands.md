---
ms.date: 09/07/2018
ms.topic: reference
title: Godkända verb för PowerShell-kommandon
description: Godkända verb för PowerShell-kommandon
ms.openlocfilehash: 237355ba9729cfe16c335b39f19ab20e40999457
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655822"
---
# <a name="approved-verbs-for-powershell-commands"></a>Godkända verb för PowerShell-kommandon

PowerShell använder ett verb-Substantiv-par för namn på cmdlets och för deras härledda .NET-klasser.
Verbets del av namnet identifierar den åtgärd som cmdleten utför. Substantiv delen av namnet identifierar den entitet som åtgärden utförs på. Till exempel `Get-Command` hämtar cmdleten alla kommandon som är registrerade i PowerShell.

> [!NOTE]
> PowerShell använder termen _verb_ för att beskriva ett ord som förutsätter en åtgärd även om ordet inte är ett standard-verb på det engelska språket. Termen _nytt_ är till exempel ett giltigt PowerShell-verb eftersom det innebär en åtgärd trots att det inte är ett verb på det engelska språket.

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->

Varje godkänt verb har ett motsvarande _alias_ definierat.
Vi använder det här aliaset i alias för kommandon som använder verbet.
Till exempel aliaset prefix för `Import` är `ip` och, och därför aliaset för `Import-Module` är `ipmo` .  Detta är en rekommendation men inte en regel. i synnerhet behöver den inte respekteras för kommando Ali Aset mimicking välkända kommandon från andra miljöer.

## <a name="verb-naming-recommendations"></a>Rekommendationer för namngivning av verb

Följande rekommendationer hjälper dig att välja ett lämpligt verb för cmdleten, för att säkerställa konsekvens mellan de cmdletar som du skapar, de cmdletar som tillhandahålls av PowerShell och de cmdletar som har utformats av andra.

- Använd ett av de fördefinierade verben som tillhandahålls av PowerShell
- Använd verbet för att beskriva det allmänna omfånget för åtgärden och Använd parametrar för att ytterligare förfina cmdletens åtgärd.
- Använd inte en synonym till ett godkänt verb. Till exempel Använd alltid `Remove` , aldrig användning `Delete` eller `Eliminate` .
- Använd endast formuläret för varje verb som anges i det här avsnittet. Använd till exempel `Get` , men Använd inte `Getting` eller `Gets` .
- Använd inte följande reserverade verb eller alias. PowerShell-språket eller en sällsynt del av dess cmdlet använder dessa verb under exceptionella omständigheter.
    - ()
    - [Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f): ordna objekt i ett angivet formulär eller en viss layout
    - [Grupp](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP): ordnar eller kopplar samman en eller flera resurser
    - [Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)
    - Sortera (SR)
    - Tee (te)
    - Var (vad än är)

Du kan få en fullständig lista över verb som använder `Get-Verb` cmdleten.

## <a name="similar-verbs-for-different-actions"></a>Liknande verb för olika åtgärder

Följande liknande verb representerar olika åtgärder.

### <a name="new-vs-set"></a>Ny vs. Set

Använd `New` verbet för att skapa en ny resurs. Använd `Set` verbet för att ändra en befintlig resurs, om den inte redan finns, t `Set-Variable` . ex. cmdleten.

### <a name="find-vs-search"></a>Sök vs. search

Använd `Find` verbet för att söka efter ett objekt. Använd `Search` verbet för att skapa en referens till en resurs i en behållare.

### <a name="get-vs-read"></a>Hämta kontra läsa

Använd `Get` verbet för att hämta information om en resurs (till exempel en fil) eller för att hämta ett objekt som du kan använda för att få åtkomst till resursen i framtiden. Använd `Read` verbet för att öppna en resurs och antingen extrahera information som finns i.

### <a name="invoke-vs-start"></a>Invoke vs. start

Använd `Invoke` verbet för att utföra synkrona åtgärder, till exempel köra ett kommando och vänta tills det har slutat. Använd `Start` verbet för att starta asynkrona åtgärder, till exempel starta en autonom process.

### <a name="ping-vs-test"></a>Ping mot test

Använd `Test` verbet.

## <a name="common-verbs"></a>Vanliga verb

PowerShell använder uppräknings klassen [system. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) för att definiera allmänna åtgärder som kan tillämpas på nästan vilken cmdlet som helst. I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|--------------------|------------|--------------|
|[Lägg till](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Lägger till en resurs i en behållare eller bifogar ett objekt till ett annat objekt. Till exempel `Add-Content` lägger cmdleten till innehåll till en fil. Verbet är länkat till `Remove` .|Lägg till, bifoga, sammanfoga, infoga|
|[Rensa](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Tar bort alla resurser från en behållare men tar inte bort behållaren. Till exempel `Clear-Content` tar cmdleten bort innehållet i en fil men tar inte bort filen.|Rensa, radera, släppa, avmarkera, unset, upphäver|
|[Stäng](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Ändrar status för en resurs så att den blir otillgänglig, otillgänglig eller oanvändbar. Verbet är länkat till `Open.`||
|[Kopiera](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Kopierar en resurs till ett annat namn eller till en annan behållare. Till exempel `Copy-Item` kopierar cmdleten ett objekt (till exempel en fil) från en plats i data lagret till en annan plats.|Duplicera, klona, replikera, synkronisera|
|[RETUR](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Anger en åtgärd som gör det möjligt för användaren att flytta till en resurs. Till exempel `Enter-PSSession` placerar cmdleten användaren i en interaktiv session. Verbet är länkat till `Exit` .|Push-överför till|
|[Avsluta](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (t ex)|Anger den aktuella miljön eller kontexten till den senast använda kontexten. Till exempel `Exit-PSSession` placerar cmdleten användaren i sessionen som användes för att starta den interaktiva sessionen. Verbet är länkat till `Enter` .|Pop, ut|
|[Sök](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Söker efter ett objekt i en behållare som är okänt, underförstådd, valfri eller angiven.|Sök|
|[Hämta](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Anger en åtgärd som hämtar en resurs. Verbet är länkat till `Set` .|Läsa, öppna, katta, skriva, dir, Hämta, dumpa, Hämta, undersöka, söka efter|
|[Dölj](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Gör en resurs okänd. Till exempel kan en-cmdlet som innehåller namnet Dölj verb dölja en tjänst från en användare. Verbet är länkat till `Show` .|Blockera|
|[Anslut](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Kombinerar resurser till en resurs. Till exempel `Join-Path` kombinerar cmdleten en sökväg med en av dess underordnade sökvägar för att skapa en enskild sökväg. Verbet är länkat till `Split` .|Kombinera, Unita, Anslut, koppla|
|[Lås](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Skyddar en resurs. Verbet är länkat till `Unlock` .|Begränsa, säkra|
|[Flytta](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Flyttar en resurs från en plats till en annan. Till exempel `Move-Item` flyttar cmdleten ett objekt från en plats i data lagret till en annan plats.|Överföring, namn, migrera|
|[Ny](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Skapar en resurs. ( `Set` Verbet kan också användas när du skapar en resurs som innehåller data, t. ex `Set-Variable` . cmdleten.)|Skapa, generera, skapa, skapa, allokera|
|[Öppna](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (OP)|Ändrar status för en resurs för att göra den tillgänglig, tillgänglig eller användbar. Verbet är länkat till `Close` .||
|[Optimera](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Ökar effektiviteten för en resurs.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Tar bort ett objekt från toppen av en stack. Till exempel `Pop-Location` ändrar cmdleten den aktuella platsen till den plats som senast skickades till stacken.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (PU)|Lägger till ett objekt överst i en stack. Till exempel push- `Push-Location` cmdleten den aktuella platsen till stacken.||
|[Gör om](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Återställer en resurs till det tillstånd som har gjorts om.||
|[Ta bort](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Tar bort en resurs från en behållare. Till exempel `Remove-Variable` tar cmdleten bort en variabel och dess värde. Verbet är länkat till `Add` .|Rensa, klippa ut, ta bort, ta bort, radera|
|[Byt namn](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Ändrar namnet på en resurs. Till exempel,- `Rename-Item` cmdleten, som används för att komma åt lagrade data, ändrar namnet på ett objekt i data lagret.|Ändra|
|[Återställ](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Återställer en resurs tillbaka till ursprungligt tillstånd.||
|[Ändra storlek](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(RZ)|Ändrar storleken på en resurs.||
|[Sök](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Skapar en referens till en resurs i en behållare.|Hitta, leta upp|
|[Välj](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Söker efter en resurs i en behållare. Till exempel `Select-String` söker cmdleten efter text i strängar och filer.|Hitta, leta upp|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Ersätter data på en befintlig resurs eller skapar en resurs som innehåller vissa data. Till exempel `Set-Date` ändrar cmdleten system tiden på den lokala datorn. ( `New` Verbet kan också användas för att skapa en resurs.) Verbet är länkat till `Get` .|Skriva, återställa, tilldela, konfigurera|
|[Visa](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (SH)|Gör en resurs synlig för användaren. Verbet är länkat till `Hide` .|Visa, producera|
|[Hoppa över](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Hoppar över en eller flera resurser eller punkter i en sekvens.|Kringgå, hoppa|
|[Dela](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Separerar delar av en resurs. Till exempel `Split-Path` returnerar cmdleten olika delar av en sökväg. Verbet är länkat till `Join` .|Särskilt|
|[Steg](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Flyttar till nästa punkt eller resurs i en sekvens.||
|[Växel](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Anger en åtgärd som växlar mellan två resurser, t. ex. för att ändra mellan två platser, ansvars områden eller tillstånd.||
|[Ångra](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (UN)|Anger en resurs till sitt tidigare tillstånd.||
|[Lås upp](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Storbritannien)|Frigör en resurs som är låst. Verbet är länkat till `Lock` .|Frigör, begränsa och ta bort skydd|
|[Titta](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Kontrollerar eller övervakar kontinuerligt en resurs efter ändringar.||

## <a name="communications-verbs"></a>Kommunikations verb

PowerShell använder klassen [system. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) för att definiera åtgärder som gäller för kommunikation. I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|--------------------|------------|--------------|
|[Anslut](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Skapar en länk mellan en källa och ett mål. Verbet är länkat till `Disconnect` .|Anslut till, Telnet|
|[Koppla från](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|Bryter länken mellan en källa och ett mål. Verbet är länkat till `Connect` .|Bryt, logga ut|
|[Läs](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Hämtar information från en källa. Verbet är länkat till `Write` .|Hämta, prompt, Hämta|
|[Ta emot](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Accepterar information som skickas från en källa. Verbet är länkat till `Send` .|Läs, Godkänn, granska|
|[Skicka](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Levererar information till ett mål. Verbet är länkat till `Receive` .|Skicka, Sänd, e-post, Fax|
|[Skriva](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Lägger till information till ett mål. Verbet är länkat till `Read` .|Lägg till, Skriv ut|

## <a name="data-verbs"></a>Dataverb

PowerShell använder klassen [system. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) för att definiera åtgärder som gäller för data hantering. I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|-------------------------|------------|--------------|
|[Säkerhets kopiering](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Lagrar data genom att replikeras.|Spara, Bränn, replikera, synkronisera|
|[Kontroll punkt](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (CH)|Skapar en ögonblicks bild av dataens aktuella tillstånd eller dess konfiguration.|Diff|
|[Jämför](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Utvärderar data från en resurs mot data från en annan resurs.|Diff|
|[Komprimera](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Komprimerar data för en resurs. Par med `Expand` .|Oftast|
|[Konvertera](/dotnet/api/System.Management.Automation.VerbsData.Convert) (ka)|Ändrar data från en representation till en annan när cmdleten stöder dubbelriktad konvertering eller när cmdleten stöder konvertering mellan flera data typer.|Ändra, ändra storlek, sampla om|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Konverterar en primär typ av indata (cmdleten Substantiv visar indata) till en eller flera typer av utdata som stöds.|Exportera, skriva ut, ut|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Konverterar från en eller flera typer av indata till en primär Utdatatyp (cmdleten Substantiv visar utdatatypen).|Importera, inmatat i|
|[Demontera](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Kopplar från en namngiven entitet från en plats. Verbet är länkat till `Mount` .|Demontera, ta bort länk|
|[Redigera](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Ändrar befintliga data genom att lägga till eller ta bort innehåll.|Ändra, uppdatera, ändra|
|[Expandera](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Återställer data för en resurs som har komprimerats till ursprungs läget. Verbet är länkat till `Compress` .|Expandera, expandera|
|[Exportera](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Kapslar in primär indata i ett beständigt data lager, till exempel en fil eller till ett Interchange Format. Verbet är länkat till `Import` .|Extrahera, säkerhetskopiera|
|[Importera](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Skapar en resurs från data som lagras i ett beständigt data lager (till exempel en fil) eller i ett Interchange Format. Till exempel `Import-CSV` importerar cmdleten data från en fil med kommaavgränsade värden (CSV) till objekt som kan användas av andra cmdletar. Verbet är länkat till `Export` .|BulkLoad, Läs in|
|[Initiera](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Förbereder en resurs för användning och ställer in den till ett standard tillstånd.|Radera, init, förnya, återskapa, initiera om, konfigurera|
|[Gräns](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Tillämpar begränsningar för en resurs.|Kvot|
|[Sammanslagning](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Skapar en enskild resurs från flera resurser.|Kombinera, förena|
|[Montera](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Bifogar en namngiven entitet till en plats. Verbet är länkat till `Dismount` .|Ansluta|
|[Ut](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Skickar data från miljön. Till exempel `Out-Printer` skickar cmdleten data till en skrivare.||
|[Publicera](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Gör en resurs tillgänglig för andra. Verbet är länkat till `Unpublish` .|Distribuera, släpp, installera|
|[Återställ](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Anger en resurs till ett fördefinierat tillstånd, till exempel ett tillstånd som anges av `Checkpoint` . Till exempel `Restore-Computer` startar cmdleten en system återställning på den lokala datorn.|Reparera, återställa, ångra, åtgärda|
|[Spara](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Bevarar data för att undvika förlust.||
|[Synkronisera](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Säkerställer att två eller flera resurser är i samma tillstånd.|Replikera, tvinga, matcha|
|[Avpublicera](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (UB)|Gör en resurs otillgänglig för andra. Verbet är länkat till `Publish` .|Avinstallera, återgå, Dölj|
|[Uppdatera](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Ger en resurs uppdaterad för att bevara dess tillstånd, riktighet, överensstämmelse eller efterlevnad. Till exempel `Update-FormatData` uppdaterar cmdleten och lägger till filer i den aktuella PowerShell-konsolen.|Uppdatera, förnya, omberäkna och indexera igen|

## <a name="diagnostic-verbs"></a>Diagnostiska verb

PowerShell använder klassen [system. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) för att definiera åtgärder som gäller diagnostik. I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|--------------------|------------|--------------|
|[Felsöka](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (dB)|Undersöker en resurs för att diagnosticera drifts problem.|Diagnostisera|
|[Mått](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identifierar resurser som används av en angiven åtgärd eller hämtar statistik om en resurs.|Beräkna, bestämma, analysera|
|[Reparera](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Återställer en resurs till ett användbart villkor|Korrigera, återställa|
|[Lösning](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Mappar en kort representation av en resurs till en mer fullständig representation.|Expandera, bestäm|
|[Testa](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Verifierar åtgärden eller konsekvensen för en resurs.|Diagnostisera, analysera, rädda, verifiera|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (TR)|Spårar aktiviteter för en resurs.|Spåra, följa, inspektera och gräva|

## <a name="lifecycle-verbs"></a>Livscykler-verb

PowerShell använder klassen [system. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) för att definiera åtgärder som gäller för livs cykeln för en resurs. I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|--------------------|------------|--------------|
|[Godkänn](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Bekräftar eller accepterar status för en resurs eller process.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Bekräftar statusen för en resurs.|Certify|
|[Bygge](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Skapar en artefakt (vanligt vis ett binärt eller dokument) av en uppsättning indatafiler (vanligt vis käll kod eller deklarativ dokument). Det här verbet lades till i PowerShell 6.||
|[Slutför](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Avslutar en åtgärd.||
|[Bekräfta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Bekräftar, verifierar eller verifierar status för en resurs eller process.|Bekräfta, Godkänn, certifiera, verifiera, verifiera|
|[Neka](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Nekar, objekt, blockerar eller motsätter sig statusen för en resurs eller process.|Blockera, objekt, neka, avvisa|
|[Distribuera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Skickar ett program, en webbplats eller en lösning till ett fjärrmål [s] på ett sådant sätt att en konsument av lösningen kan komma åt den när distributionen har slutförts. Det här verbet lades till i PowerShell 6.||
|[Inaktivera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Konfigurerar en resurs till ett otillgängligt eller inaktivt tillstånd. Till exempel `Disable-PSBreakpoint` gör cmdleten en inaktiv Bryt punkt. Verbet är länkat till `Enable` .|Stoppa, Dölj|
|[Aktivera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Konfigurerar en resurs till ett tillgängligt eller aktivt tillstånd. Till exempel `Enable-PSBreakpoint` gör cmdleten en aktiv Bryt punkt. Verbet är länkat till `Disable` .|Starta, börja|
|[Installera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (är)|Placerar en resurs på en plats och eventuellt initierar den. Verbet är länkat till `Uninstall` .|Installation|
|[Anropa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Utför en åtgärd, till exempel köra ett kommando eller en metod.|Kör, starta|
|[Registrera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Skapar en post för en resurs i en lagrings plats, till exempel en databas. Verbet är länkat till `Unregister` .||
|[Begäran](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|Frågar efter en resurs eller ber om behörighet.||
|[Starta om](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Stoppar en åtgärd och startar sedan den igen. Till exempel `Restart-Service` stoppas cmdleten och startar sedan en tjänst.|Pappers|
|[Fortsätt](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Startar en åtgärd som har pausats. Till exempel `Resume-Service` startar cmdleten en tjänst som har pausats. Verbet är länkat till `Suspend` .||
|[Starta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Initierar en åtgärd. Till exempel `Start-Service` startar cmdleten en tjänst. Verbet är länkat till `Stop` .|Starta, initiera, starta|
|[Stoppa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|Avvecklar en aktivitet. Verbet är länkat till `Start` .|Avsluta, avsluta, Avbryt|
|[Skicka](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Visar en resurs för godkännande.|Skicka|
|[Pausa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Pausar en aktivitet. Till exempel `Suspend-Service` pausar cmdleten en tjänst. Verbet är länkat till `Resume` .|Pausa|
|[Avinstallera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (US)|Tar bort en resurs från en angiven plats. Verbet är länkat till `Install` .||
|[Avregistrera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (din)|Tar bort posten för en resurs från en lagrings plats. Verbet är länkat till `Register` .|Ta bort|
|[Vänta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Pausar en åtgärd tills en angiven händelse inträffar. Cmdleten kan till exempel `Wait-Job` pausa åtgärder tills ett eller flera bakgrunds jobb är slutförda.|Vilo läge, pausa|

## <a name="security-verbs"></a>Säkerhetsverb

PowerShell använder klassen [system. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) för att definiera åtgärder som ska vidtas för säkerhet. I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|--------------------|------------|--------------|
|[Blockera](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Begränsar åtkomsten till en resurs. Verbet är länkat till `Unblock` .|Förhindra, begränsa, neka|
|[Bevilja](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Tillåter åtkomst till en resurs. Verbet är länkat till `Revoke` .|Tillåt, aktivera|
|[Skydda](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Skyddar en resurs från angrepp eller förlust. Verbet är länkat till `Unprotect` .|Kryptera, skydda, försegla|
|[Återkalla](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (lib)|Anger en åtgärd som inte tillåter åtkomst till en resurs. Verbet är länkat till `Grant` .|Ta bort, inaktivera|
|[Avblockera](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Tar bort begränsningar för en resurs. Verbet är länkat till `Block` .|Rensa, Tillåt|
|[Ta bort skydd](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (upp)|Tar bort skydd från en resurs som har lagts till för att förhindra angrepp eller förlust. Verbet är länkat till `Protect` .|Dekryptera, avförslut|

## <a name="other-verbs"></a>Andra verb

PowerShell använder klassen [system. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) för att definiera kanoniska verb som inte passar in i en viss kategori för verb, till exempel verben common, Communications, data, Lifecycle eller Security verb.

|Verb (alias)|Åtgärd|Synonymer för att undvika|
|--------------------|------------|--------------|
|[Använd](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Använder eller innehåller en resurs för att göra något.||

## <a name="see-also"></a>Se även

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)
- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)
- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)
- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)
- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)
- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)
- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)
- [Cmdlet-deklaration](./cmdlet-class-declaration.md)
- [Programmeringsguide för Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)
- [Windows PowerShell Shell SDK](../windows-powershell-reference.md)
