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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359470"
---
# <a name="approved-verbs-for-powershell-commands"></a>Godkända verb för PowerShell-kommandon

PowerShell använder ett verb-Substantiv-par för namn på cmdlets och för deras härledda Microsoft .NET Framework-klasser.
`Get-Command`-cmdleten som tillhandahålls av PowerShell används till exempel för att hämta alla kommandon som är registrerade i PowerShell.
Verbets del av namnet identifierar den åtgärd som cmdleten utför.
Substantiv delen av namnet identifierar den entitet som åtgärden utförs på.

> [!NOTE]
> PowerShell använder termen *verb* för att beskriva ett ord som förutsätter en åtgärd även om ordet inte är ett standard-verb på det engelska språket.
> Termen *nytt* är till exempel ett giltigt PowerShell-verb eftersom det innebär en åtgärd trots att det inte är ett verb på det engelska språket.

## <a name="verb-naming-rules"></a>Namngivnings regler för verb

Följande lista innehåller rikt linjer som du bör tänka på när du väljer verbet för ett cmdlet-namn:

* När du anger verbet rekommenderar vi att du använder ett av de fördefinierade verben som tillhandahålls av PowerShell (alias för dessa fördefinierade verb ingår i följande tabeller).
  När du använder ett fördefinierat verb garanterar du konsekvens mellan de cmdletar som du skapar, de cmdletar som tillhandahålls av PowerShell och de cmdlets som har utformats av andra.

* Använd de fördefinierade verben för att beskriva den allmänna omfattningen av åtgärden och Använd parametrar för att ytterligare förfina cmdletens åtgärd.

* Om du vill framtvinga konsekvens över cmdletar ska du inte använda en synonym till ett godkänt verb.

* Använd endast formuläret för varje verb som anges i det här avsnittet.
  Använd till exempel "Get", men Använd inte "Hämta" eller "får".

* Använd Pascal-hölje för verb.
  I Pascal-hölje är den första bokstaven i varje ord kapitaliserad, till exempel "Sol".

* Använd inte följande reserverade verb eller alias.
  Dessa verb används av PowerShell-språket eller av särskilda Case-cmdletar från PowerShell.
  - ()
  - Format (f)
  - Grupp (GP)
  - Sortera (SR)
  - Tee (te)
  - Var (vad än är)

## <a name="similar-verbs-for-different-actions"></a>Liknande verb för olika åtgärder

Följande liknande verb representerar olika åtgärder.

### <a name="new-vs-set"></a>Ny vs. Set
`New` verbet används för att skapa en ny resurs.
`Set` verbet används för att ändra en befintlig resurs, om du vill kan du skapa resursen om den inte finns, till exempel `Set-Variable`-cmdlet.

### <a name="find-vs-search"></a>Sök vs. search
`Find` verbet används för att söka efter ett objekt.
`Search` verbet används för att skapa en referens till en resurs i en behållare.

### <a name="get-vs-read"></a>Hämta kontra läsa
`Get` verbet används för att hämta en resurs, till exempel en fil.
`Read` verbet används för att hämta information från en källa, till exempel en fil.

### <a name="invoke-vs-start"></a>Invoke vs. start
`Invoke` verbet används för att utföra en åtgärd som vanligt vis är en synkron åtgärd, till exempel köra ett kommando.
`Start` verbet används för att påbörja en åtgärd som vanligt vis är en asynkron åtgärd, till exempel starta en process.

### <a name="ping-vs-test"></a>Ping mot test
Använd `Test` verbet.

## <a name="common-verbs"></a>Vanliga verb

PowerShell använder uppräknings klassen [system. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) för att definiera allmänna åtgärder som kan tillämpas på nästan vilken cmdlet som helst.
I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Lägg till](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Lägger till en resurs i en behållare eller bifogar ett objekt till ett annat objekt. Till exempel lägger `Add-Content`-cmdleten till innehåll i en fil. Verbet är länkat till `Remove`.|För den här åtgärden ska du inte använda verb som Lägg till, bifoga, sammanfoga eller infoga.|
|[Rensa](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Tar bort alla resurser från en behållare men tar inte bort behållaren. Till exempel tar cmdleten `Clear-Content` bort innehållet i en fil men tar inte bort filen.|För den här åtgärden ska du inte använda verb som flush, Erase, release, avmarkera, unset eller upphäver.|
|[Stäng](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Ändrar status för en resurs så att den blir otillgänglig, otillgänglig eller oanvändbar. Verbet är länkat till `Open.`||
|[Kopiera](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Kopierar en resurs till ett annat namn eller till en annan behållare. Till exempel, `Copy-Item`-cmdleten som används för att komma åt lagrade data, kopierar ett objekt från en plats i data lagret till en annan plats.|För den här åtgärden ska du inte använda verb som duplicera, klona, replikera eller synkronisera.|
|[RETUR](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Anger en åtgärd som gör det möjligt för användaren att flytta till en resurs. `Enter-PSSession`-cmdleten placerar till exempel användaren i en interaktiv session. Verbet är länkat till `Exit`.|Använd inte verb som push eller Into för den här åtgärden.|
|[Avsluta](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (t ex)|Anger den aktuella miljön eller kontexten till den senast använda kontexten. Till exempel placerar `Exit-PSSession`-cmdlet användaren i sessionen som användes för att starta den interaktiva sessionen. Verbet är länkat till `Enter`.|För den här åtgärden ska du inte använda verb som pop eller out.|
|[Sök](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Söker efter ett objekt i en behållare som är okänt, underförstådd, valfri eller angiven.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Ordnar objekt i en angiven form eller layout.||
|[Hämta](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Anger en åtgärd som hämtar en resurs. Verbet är länkat till `Set`.|För den här åtgärden ska du inte använda verb som läsa, öppna, katt, typ, dir, Hämta, dumpa, Hämta, granska, söka eller söka.|
|[Dölj](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Gör en resurs okänd. Till exempel kan en-cmdlet som innehåller namnet Dölj verb dölja en tjänst från en användare. Verbet är länkat till `Show`.|Använd inte ett verb, till exempel block, för den här åtgärden.|
|[Anslut](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Kombinerar resurser till en resurs. Till exempel kombinerar cmdleten `Join-Path` en sökväg med en av dess underordnade sökvägar för att skapa en enskild sökväg. Verbet är länkat till `Split`.|För den här åtgärden ska du inte använda verb som kombinera, Unita, Connect eller Association.|
|[Lås](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Skyddar en resurs. Verbet är länkat till `Unlock`.|För den här åtgärden ska du inte använda verb som begränsa eller skydda.|
|[Flytta](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Flyttar en resurs från en plats till en annan. `Move-Item`-cmdleten flyttar till exempel ett objekt från en plats i data lagret till en annan plats.|För den här åtgärden ska du inte använda verb som överföring, namn eller migrera.|
|[Ny](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Skapar en resurs. (`Set` verbet kan också användas när du skapar en resurs som innehåller data, till exempel `Set-Variable`-cmdleten.)|För den här åtgärden ska du inte använda verb som skapa, skapa, skapa, skapa eller allokera.|
|[Öppna](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (OP)|Ändrar status för en resurs för att göra den tillgänglig, tillgänglig eller användbar. Verbet är länkat till `Close`.||
|[Optimera](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Ökar effektiviteten för en resurs.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Tar bort ett objekt från toppen av en stack. `Pop-Location`-cmdleten ändrar till exempel den aktuella platsen till den plats som senast skickades till stacken.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (PU)|Lägger till ett objekt överst i en stack. Till exempel pushar `Push-Location` cmdleten den aktuella platsen till stacken.||
|[Gör om](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Återställer en resurs till det tillstånd som har gjorts om.||
|[Ta bort](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Tar bort en resurs från en behållare. Till exempel tar cmdleten `Remove-Variable` bort en variabel och dess värde. Verbet är länkat till `Add`.|För den här åtgärden ska du inte använda verb som rensa, klipp ut, ta bort, ignorera eller radera.|
|[Byt namn](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Ändrar namnet på en resurs. Till exempel är `Rename-Item`-cmdleten, som används för att komma åt lagrade data, ändra namnet på ett objekt i data lagret.|Använd inte ett verb, till exempel Change, för den här åtgärden.|
|[Återställ](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Återställer en resurs tillbaka till ursprungligt tillstånd.||
|[Sök](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Skapar en referens till en resurs i en behållare.|För den här åtgärden ska du inte använda verb som Sök eller hitta.|
|[Välj](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Söker efter en resurs i en behållare. Till exempel söker cmdleten `Select-String` efter text i strängar och filer.|För den här åtgärden ska du inte använda verb som Sök eller hitta.|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Ersätter data på en befintlig resurs eller skapar en resurs som innehåller vissa data. `Set-Date`-cmdleten ändrar till exempel system tiden på den lokala datorn. (`New` verbet kan också användas för att skapa en resurs.) Verbet är länkat till `Get`.|För den här åtgärden ska du inte använda verb som skriva, återställa, tilldela eller konfigurera.|
|[Visa](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (SH)|Gör en resurs synlig för användaren. Verbet är länkat till `Hide`.|För den här åtgärden ska du inte använda verb som visning eller framställning.|
|[Hoppa över](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Hoppar över en eller flera resurser eller punkter i en sekvens.|För den här åtgärden ska du inte använda ett verb som bypass eller hoppa.|
|[Dela](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Separerar delar av en resurs. Till exempel returnerar `Split-Path`-cmdleten olika delar av en sökväg. Verbet är länkat till `Join`.|Använd inte något annat verb för den här åtgärden.|
|[Steg](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Flyttar till nästa punkt eller resurs i en sekvens.||
|[Växel](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Anger en åtgärd som växlar mellan två resurser, t. ex. för att ändra mellan två platser, ansvars områden eller tillstånd.||
|[Ångra](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (UN)|Anger en resurs till sitt tidigare tillstånd.||
|[Lås upp](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Storbritannien)|Frigör en resurs som är låst. Verbet är länkat till `Lock`.|För den här åtgärden ska du inte använda verb som release, unstrict eller unsecure.|
|[Titta](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Kontrollerar eller övervakar kontinuerligt en resurs efter ändringar.||

## <a name="communications-verbs"></a>Kommunikations verb

PowerShell använder klassen [system. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) för att definiera åtgärder som gäller för kommunikation.
I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Anslut](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Skapar en länk mellan en källa och ett mål. Verbet är länkat till `Disconnect`.|För den här åtgärden ska du inte använda verb som JOIN eller Telnet.|
|[Koppla från](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|Bryter länken mellan en källa och ett mål. Verbet är länkat till `Connect`.|För den här åtgärden ska du inte använda verb som Break eller LOGOFF.|
|[Läs](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Hämtar information från en källa. Verbet är länkat till `Write`.|För den här åtgärden ska du inte använda verb som Hämta, uppmana eller hämta.|
|[Ta emot](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Accepterar information som skickas från en källa. Verbet är länkat till `Send`.|För den här åtgärden ska du inte använda verb som läsa, acceptera eller granska.|
|[Skicka](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Levererar information till ett mål. Verbet är länkat till `Receive`.|För den här åtgärden ska du inte använda verb som skicka, Sänd, e-post eller fax.|
|[Skriva](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Lägger till information till ett mål. Verbet är länkat till `Read`.|För den här åtgärden ska du inte använda verb som Spara eller skriva ut.|

## <a name="data-verbs"></a>Dataverb

PowerShell använder klassen [system. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) för att definiera åtgärder som gäller för data hantering.
I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Kommentar|
|-------------------------|------------|--------------|
|[Säkerhets kopiering](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Lagrar data genom att replikeras.|För den här åtgärden ska du inte använda verb som Spara, Bränn, replikera eller synkronisera.|
|[Kontroll punkt](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (CH)|Skapar en ögonblicks bild av dataens aktuella tillstånd eller dess konfiguration.|Använd inte ett verb, till exempel diff, för den här åtgärden.|
|[Jämför](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Utvärderar data från en resurs mot data från en annan resurs.|Använd inte ett verb, till exempel diff, för den här åtgärden.|
|[Komprimera](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Komprimerar data för en resurs. Par med `Expand`.|Använd inte ett verb, till exempel komprimera, för den här åtgärden.|
|[Konvertera](/dotnet/api/System.Management.Automation.VerbsData.Convert) (ka)|Ändrar data från en representation till en annan när cmdleten stöder dubbelriktad konvertering eller när cmdleten stöder konvertering mellan flera data typer.|För den här åtgärden ska du inte använda verb som ändra, ändra storlek eller sampla om.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Konverterar en primär typ av indata (cmdleten Substantiv visar indata) till en eller flera typer av utdata som stöds.|För den här åtgärden ska du inte använda verb som export, output eller out.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Konverterar från en eller flera typer av indata till en primär Utdatatyp (cmdleten Substantiv visar utdatatypen).|För den här åtgärden ska du inte använda verb som import, indatamängd eller in.|
|[Demontera](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Kopplar från en namngiven entitet från en plats. Verbet är länkat till `Mount`.|För den här åtgärden ska du inte använda verb som demontera eller ta bort länk.|
|[Redigera](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Ändrar befintliga data genom att lägga till eller ta bort innehåll.|För den här åtgärden ska du inte använda verb som ändra, uppdatera eller ändra.|
|[Expandera](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Återställer data för en resurs som har komprimerats till ursprungs läget. Verbet är länkat till `Compress`.|För den här åtgärden ska du inte använda verb som explodera eller expandera.|
|[Exportera](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Kapslar in primär indata i ett beständigt data lager, till exempel en fil eller till ett Interchange Format. Verbet är länkat till `Import`.|För den här åtgärden ska du inte använda verb som extrahera eller säkerhetskopiera.|
|[Grupp](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP)|Ordnar eller associerar en eller flera resurser.|För den här åtgärden ska du inte använda verb som agg regering, arrangera, associera eller korrelera.|
|[Importera](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Skapar en resurs från data som lagras i ett beständigt data lager (till exempel en fil) eller i ett Interchange Format. `Import-CSV`-cmdlet importerar till exempel data från en fil med kommaavgränsade värden (CSV) till objekt som kan användas av andra cmdletar. Verbet är länkat till `Export`.|För den här åtgärden ska du inte använda verb som BulkLoad eller load.|
|[Initiera](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Förbereder en resurs för användning och ställer in den till ett standard tillstånd.|För den här åtgärden ska du inte använda verb som radera, init, förnya, återskapa, initiera om eller konfigurera.|
|[Gräns](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Tillämpar begränsningar för en resurs.|Använd inte ett verb som kvot för den här åtgärden.|
|[Sammanslagning](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Skapar en enskild resurs från flera resurser.|För den här åtgärden ska du inte använda verb som kombinera eller delta.|
|[Montera](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Bifogar en namngiven entitet till en plats. Verbet är länkat till `Dismount`.|Använd inte verbet Connect för att utföra den här åtgärden.|
|[Ut](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Skickar data från miljön. Till exempel skickar `Out-Printer`-cmdleten data till en skrivare.||
|[Publicera](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Gör en resurs tillgänglig för andra. Verbet är länkat till `Unpublish`.|För den här åtgärden ska du inte använda verb som distribuera, frigör eller installera.|
|[Återställ](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Anger en resurs till ett fördefinierat tillstånd, till exempel ett tillstånd som anges av `Checkpoint`. `Restore-Computer`-cmdleten startar till exempel en system återställning på den lokala datorn.|För den här åtgärden ska du inte använda verb som Repair, Return, Undo eller Fix.|
|[Spara](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Bevarar data för att undvika förlust.||
|[Synkronisera](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Säkerställer att två eller flera resurser är i samma tillstånd.|För den här åtgärden ska du inte använda verb som replikera, tvinga eller matcha.|
|[Avpublicera](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (UB)|Gör en resurs otillgänglig för andra. Verbet är länkat till `Publish`.|För den här åtgärden ska du inte använda verb som avinstallera, Återställ eller Dölj.|
|[Uppdatera](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Ger en resurs uppdaterad för att bevara dess tillstånd, riktighet, överensstämmelse eller efterlevnad. Till exempel uppdaterar `Update-FormatData` cmdleten och lägger till filer i den aktuella PowerShell-konsolen.|För den här åtgärden ska du inte använda verb som uppdatera, förnya, beräkna om eller indexera om.|

## <a name="diagnostic-verbs"></a>Diagnostiska verb

PowerShell använder klassen [system. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) för att definiera åtgärder som gäller diagnostik.
I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Felsöka](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (dB)|Undersöker en resurs för att diagnosticera drifts problem.|Använd inte ett verb, till exempel diagnostisera, för den här åtgärden.|
|[Mått](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identifierar resurser som används av en angiven åtgärd eller hämtar statistik om en resurs.|För den här åtgärden ska du inte använda verb som beräkna, Bestäm eller analysera.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)|Använd `Test` verbet.||
|[Reparera](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Återställer en resurs till ett användbart villkor|För den här åtgärden ska du inte använda verb som Fix eller Restore.|
|[Lösning](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Mappar en kort representation av en resurs till en mer fullständig representation.|För den här åtgärden ska du inte använda verb som Expand eller Bestäm.|
|[Testa](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Verifierar åtgärden eller konsekvensen för en resurs.|För den här åtgärden ska du inte använda verb som diagnostisera, analysera, rädda eller verifiera.|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (TR)|Spårar aktiviteter för en resurs.|För den här åtgärden ska du inte använda verb som spåra, följa, inspektera eller gräva.|

## <a name="lifecycle-verbs"></a>Livscykler-verb

PowerShell använder klassen [system. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) för att definiera åtgärder som gäller för livs cykeln för en resurs.
I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Godkänn](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Bekräftar eller accepterar status för en resurs eller process.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Bekräftar statusen för en resurs.|Använd inte ett verb som certifiera för den här åtgärden.|
|[Bygge](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Skapar en artefakt (vanligt vis ett binärt eller dokument) av en uppsättning indatafiler (vanligt vis käll kod eller deklarativ dokument)|Det här verbet har lagts till i PowerShell V6|
|[Slutför](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Avslutar en åtgärd.||
|[Bekräfta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Bekräftar, verifierar eller verifierar status för en resurs eller process.|För den här åtgärden ska du inte använda verb som bekräfta, Godkänn, certifiera, verifiera eller verifiera.|
|[Neka](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Nekar, objekt, blockerar eller motsätter sig statusen för en resurs eller process.|För den här åtgärden ska du inte använda verb som blockera, objekt, neka eller avvisa.|
|[Distribuera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Skickar ett program, en webbplats eller en lösning till ett fjärrmål [s] på ett sådant sätt att en konsument av lösningen kan komma åt den när distributionen har slutförts|Det här verbet har lagts till i PowerShell V6|
|[Inaktivera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Konfigurerar en resurs till ett otillgängligt eller inaktivt tillstånd. `Disable-PSBreakpoint`-cmdleten gör till exempel en Bryt punkt inaktiv. Verbet är länkat till `Enable`.|Använd inte verb som stanna eller Dölj för den här åtgärden.|
|[Aktivera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Konfigurerar en resurs till ett tillgängligt eller aktivt tillstånd. `Enable-PSBreakpoint`-cmdleten gör till exempel en Bryt punkt aktiv. Verbet är länkat till `Disable`.|För den här åtgärden ska du inte använda verb som start eller BEGIN.|
|[Installera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (är)|Placerar en resurs på en plats och eventuellt initierar den. Verbet är länkat till `Uninstall`.|För den här åtgärden ska du inte använda verb som installation.|
|[Anropa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Utför en åtgärd, till exempel köra ett kommando eller en metod.|För den här åtgärden ska du inte använda verb som kör eller starta.|
|[Registrera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Skapar en post för en resurs i en lagrings plats, till exempel en databas. Verbet är länkat till `Unregister`.||
|[Begäran](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|Frågar efter en resurs eller ber om behörighet.||
|[Starta om](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Stoppar en åtgärd och startar sedan den igen. Till exempel stoppas `Restart-Service`-cmdleten och startar sedan en tjänst.|Använd inte ett verb, till exempel Recycle, för den här åtgärden.|
|[Fortsätt](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Startar en åtgärd som har pausats. `Resume-Service`-cmdleten startar till exempel en tjänst som har pausats. Verbet är länkat till `Suspend`.||
|[Starta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Initierar en åtgärd. `Start-Service`-cmdleten startar till exempel en tjänst. Verbet är länkat till `Stop`.|För den här åtgärden ska du inte använda verb som starta, initiera eller starta.|
|[Stoppa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|Avvecklar en aktivitet. Verbet är länkat till `Start`.|För den här åtgärden ska du inte använda verb som End, Kill, Terminate eller Cancel.|
|[Skicka](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Visar en resurs för godkännande.|Använd inte ett verb, till exempel post, för den här åtgärden.|
|[Pausa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Pausar en aktivitet. Till exempel pausar `Suspend-Service` cmdleten en tjänst. Verbet är länkat till `Resume`.|För den här åtgärden ska du inte använda ett verb som Pause.|
|[Avinstallera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (US)|Tar bort en resurs från en angiven plats. Verbet är länkat till `Install`.||
|[Avregistrera](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (din)|Tar bort posten för en resurs från en lagrings plats. Verbet är länkat till `Register`.|För den här åtgärden ska du inte använda ett verb som ta bort.|
|[Vänta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Pausar en åtgärd tills en angiven händelse inträffar. Till exempel pausar `Wait-Job` cmdleten åtgärder tills ett eller flera bakgrunds jobb har slutförts.|För den här åtgärden ska du inte använda verb som vilo läge eller paus.|

## <a name="security-verbs"></a>Säkerhetsverb

PowerShell använder klassen [system. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) för att definiera åtgärder som ska vidtas för säkerhet.
I följande tabell visas de flesta av de definierade verben.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Blockera](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Begränsar åtkomsten till en resurs. Verbet är länkat till `Unblock`.|För den här åtgärden ska du inte använda verb som förhindra, begränsa eller neka.|
|[Bevilja](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Tillåter åtkomst till en resurs. Verbet är länkat till `Revoke`.|Använd inte verb som Tillåt eller aktivera för den här åtgärden.|
|[Skydda](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Skyddar en resurs från angrepp eller förlust. Verbet är länkat till `Unprotect`.|För den här åtgärden ska du inte använda verb som kryptera, skydda eller försegla.|
|[Återkalla](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (lib)|Anger en åtgärd som inte tillåter åtkomst till en resurs. Verbet är länkat till `Grant`.|För den här åtgärden ska du inte använda verb som ta bort eller inaktivera.|
|[Avblockera](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Tar bort begränsningar för en resurs. Verbet är länkat till `Block`.|För den här åtgärden ska du inte använda verb som Clear eller Allow.|
|[Ta bort skydd](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (upp)|Tar bort skydd från en resurs som har lagts till för att förhindra angrepp eller förlust. Verbet är länkat till `Protect`.|För den här åtgärden ska du inte använda verb som dekryptera eller ta ur segling.|

## <a name="other-verbs"></a>Andra verb

PowerShell använder klassen [system. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) för att definiera kanoniska verb som inte passar in i en viss kategori för verb, till exempel verben common, Communications, data, Lifecycle eller Security verb.

|Verb (alias)|Åtgärd|Kommentar|
|--------------------|------------|--------------|
|[Använd](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Använder eller innehåller en resurs för att göra något.||

## <a name="see-also"></a>Se även

[System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet-deklaration](./cmdlet-class-declaration.md)

[Windows PowerShell Programmer ' s guide](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
