---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Vad är nytt i Windows PowerShell 5,0
ms.openlocfilehash: 59ccc83c7d4736181f13b72c4d3725694f80c1c8
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90847042"
---
# <a name="whats-new-in-windows-powershell-50"></a>Vad är nytt i Windows PowerShell 5,0

Windows PowerShell 5,0 innehåller viktiga nya funktioner som utökar användningen, förbättrar dess användbarhet och gör att du kan styra och hantera Windows-baserade miljöer enklare och mer omfattande.

Windows PowerShell 5,0 är bakåtkompatibelt. Cmdlets, providers, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 4,0, Windows PowerShell 3,0 och Windows PowerShell 2,0 fungerar vanligt vis i Windows PowerShell 5,0 utan ändringar.

## <a name="installing-windows-powershell"></a>Installera Windows PowerShell

Windows PowerShell 5,0 installeras som standard på Windows Server 2016 Technical Preview och Windows
10.

Installera Windows PowerShell 5,0 på Windows Server 2012 R2, Windows 8,1 Enterprise eller Windows 8,1 Pro genom att hämta och installera [Windows Management Framework 5,0](https://aka.ms/wmf5download). Se till att läsa informationen om hämtningen och uppfyller alla system krav innan du installerar Windows Management Framework 5,0.

## <a name="in-this-topic"></a>I det här avsnittet

- [Windows PowerShell 4,0 DSC-uppdateringar i KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nya funktioner i Windows PowerShell 5,0](#new-features-in-windows-powershell-50)
- [Nya funktioner i Windows PowerShell 4,0](#new-features-in-windows-powershell-40)
- [Nya funktioner i Windows PowerShell 3,0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Uppdateringar för Windows PowerShell 4,0 i november 2014 Samlad uppdatering (KB 3000850)

Många uppdateringar och förbättringar av Windows PowerShell Desired State Configuration (DSC) i Windows PowerShell 4,0 finns i den [samlade uppdateringen 2014 november för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850). Du kan kontrol lera om KB 3000850 är installerat i systemet genom att köra `Get-Hotfix -Id KB3000850` i Windows PowerShell.

- Uppdateringar av befintliga cmdletar i [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) -modulen
  - [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration) är snabbare (särskilt i ISE).
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) har en ny parameter,-UseExisting, som tillämpar den senast tillämpade konfigurationen igen.
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) -Force har åtgärd ATS.
  - [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration) visar mer värdefull information om motorns tillstånd.
  - [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) returnerar nu dator namnet tillsammans med true eller false.
  - [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration) stöder nu UNC-sökvägar.

- Nya cmdletar i [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) -modulen
  - [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration): utför en kontroll av hämtnings servern på begäran.
  - [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration): stoppar en konfiguration som redan körs.
  - [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument): gör att du kan ta bort konfigurations dokument i olika steg (väntar, föregående eller aktuella).

- Språk förbättringar
  - DependsOn stöder nu sammansatta resurser.
  - DependsOn stöder nu nummer i resurs instans namn.
  - Node-uttryck som utvärderas som tomma returnerar inte längre fel.
  - Ett fel som inträffar om ett Node-uttryck utvärderas som tomt har åtgärd ATS.
  - Konfigurationer som anropar konfigurationer fungerar nu i Windows PowerShell-konsolen.

- Förbättringar i pull-läge
  - Pull-läget stöder nu alla ZIP-filer.
  - **AllowModuleOverwrite** fungerar nu som den ska.

- Förbättringar av återhämtning
  - Med ny **DebugMode** kan du läsa in resurspooler igen.
  - Om ett konfigurations fel inträffar tas inte den väntande MOF-filen bort.
  - Den lokala Configuration Manager (LCM) är nu mer flexibel när metaconfiguration-inställningarna har skadats.

- Diagnostiska förbättringar
  - En varning visas när LCM anger timern till olika inställningar än du har angett.
  - Loggfiler innehåller nu anrops stacken för Windows PowerShell-resurser.

- Flexibilitets förbättringar
  - LocalConfigurationManager-resursen har en ny egenskap, **ActionAfterReboot**.
    - ContinueConfiguration (standardvärde): återupptar automatiskt en konfiguration när en målnod har startats om.
    - StopConfiguration: återupptar inte automatiskt en konfiguration när en nod har startats om.
  - En konsekvens körning kan nu ske oftare än en PULL-åtgärd eller vice versa.
  - Stöd för versions hantering: DSC kan nu identifiera ett dokument som har genererats på en nyare klient (ingår i [WMF 5,0](https://aka.ms/wmf5download)).

- Förbättringar av fel skydd
  - Module-versionen tillämpas nu innan en konfiguration tillämpas.
  - **DebugPreference** är nu korrekt för Get-, set-eller test-TargetResource-anrop.

- Förbättringar av hantering av autentiseringsuppgifter
  - Ett certifikat används nu, om både **certifikat** och **PSDscAllowPlainTextPassword** har angetts.
  - Autentiseringsuppgifterna dekrypteras även för Get-TargetResource.
  - Metaconfiguration-autentiseringsuppgifter krypteras och dekrypteras.
  - PSCredentials dekrypteras nu när de finns i ett inbäddat objekt.

- Inbyggda resurs förbättringar
  - Paket resursen
    - Installerar inte längre fel paket (antingen från lokala eller webb adresser).
    - Stöder nu HTTPS.
  - Det finns nu stöd för HTTPS i [paket resursen](/powershell/scripting/dsc/reference/resources/windows/packageresource).
  - [Arkiv resursen](/powershell/scripting/dsc/reference/resources/windows/archiveresource) stöder nu autentiseringsuppgifter.

## <a name="new-features-in-windows-powershell-50"></a>Nya funktioner i Windows PowerShell 5,0

- [Nya funktioner i Windows PowerShell](#new-features-in-windows-powershell)
- [Nya funktioner i Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nya funktioner i Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nya funktioner i Windows PowerShell-webbtjänster](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Viktiga fel korrigeringar i Windows PowerShell 5,0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nya funktioner i Windows PowerShell

- Från och med Windows PowerShell 5,0 kan du utveckla med hjälp av klasser, med hjälp av formell syntax och semantik som liknar andra objektorienterade programmeringsspråk. **Klass**, **Enum**och andra nyckelord har lagts till i Windows PowerShell-språket för att stödja den nya funktionen.
  Mer information om hur du arbetar med klasser finns about_Classes.

- Windows PowerShell 5,0 introducerar en ny strukturerad informations ström som du kan använda för att skicka strukturerade data mellan ett skript och dess anropare (eller värd miljö). Nu kan du använda Write-Host för att generera utdata till informations strömmen. Informations strömmar fungerar också för PowerShell. Streams, Jobs, schemalagda jobb och arbets flöden. Följande funktioner stöder informations strömmen.
  - En ny cmdlet för skrivnings information som gör att du kan ange hur Windows PowerShell hanterar informations data strömmar för ett kommando. Write-Host är en omslutning av Skriv information. Skriv information är också en arbets flödes aktivitet som stöds.
  - Med två nya vanliga parametrar, InformationVariable och InformationAction, kan du bestämma hur informations strömmar från ett kommando visas. Giltiga värden för InformationAction är SilentlyContinue, stoppa, Fortsätt, fråga, ignorera eller pausa, med SilentlyContinue som standard. InformationVariable anger en sträng som namnet på en variabel till vilken du vill att skrivnings värds data från ett kommando ska sparas.
  - En ny Preference-variabel, InformationPreference, anger din standard inställning för informations data strömmar i en Windows PowerShell-session. Standardvärdet är SilentlyContinue.
  - Två nya gemensamma arbets flödes parametrar, PSInformation och InformationAction, har lagts till.
  - När du använder kommandot Format-Table formateras nu tabell kolumner automatiskt genom att utvärdera den första 300ms av data som passerar genom data strömmen.

- I samarbete med [Microsoft Research](https://research.microsoft.com/)har en ny cmdlet, ConvertFrom-sträng, lagts till. Med ConvertFrom-sträng kan du extrahera och parsa strukturerade objekt från innehållet i text strängar. Mer information finns i ConvertFrom-String.
- En ny cmdlet för Convert-sträng formaterar automatiskt text baserat på ett exempel som du anger i en-exempel-parameter.
- En ny modul, Microsoft. PowerShell. Archive, innehåller cmdletar som gör att du kan komprimera filer och mappar till Arkiv (kallas även ZIP-filer), extrahera filer från befintliga ZIP-filer och uppdatera ZIP-filer med nyare versioner av filerna komprimerade i dem.
- Med en ny modul, PackageManagement, kan du identifiera och installera program varu paket på Internet.
  Modulen PackageManagement (tidigare OneGet) är en hanterare eller multiplexor för befintliga paket hanterare (kallas även paket leverantörer) för att enhetlig hantering av Windows-paket med ett enda Windows PowerShell-gränssnitt.
- Med en ny modul, PowerShellGet, kan du hitta, installera, publicera och uppdatera moduler och DSC-resurser på [PowerShell-galleriet](https://www.powershellgallery.com/)eller på en intern moduls lagrings plats som du kan konfigurera genom att köra cmdleten register-PSRepository.
- Ett nytt språk nyckelord, **dolt**, har lagts till för att ange att en medlem (en egenskap eller en metod) inte visas som standard i Get-Member-resultat (om du inte lägger till parametern-Force).
  Egenskaper eller metoder som har marker ATS som dolda visas inte heller i IntelliSense-resultat, om du inte är i ett sammanhang där medlemmen ska vara synlig. till exempel bör den automatiska variabeln $This Visa dolda medlemmar i klass metoden.
- New-item, remove-item och get-ChildItem har förbättrats för att stödja skapande och hantering av [symboliska länkar](https://en.wikipedia.org/wiki/Symbolic_link). Parametern **-itemType** för New-item accepterar ett nytt värde, **SymbolicLink**. Nu kan du skapa symboliska länkar på en enda rad genom att köra cmdleten New-Item.
- Get-ChildItem har också en ny djup-parameter som du använder med parametern-rekursivt för att begränsa rekursion. Get-ChildItem-rekursivt-djup 2 returnerar till exempel resultat från den aktuella mappen, alla underordnade mappar i den aktuella mappen och alla mappar i de underordnade mapparna.
- Med kopiera objekt kan du nu kopiera filer eller mappar från en Windows PowerShell-session till en annan, vilket innebär att du kan kopiera filer till sessioner som är anslutna till fjärrdatorer, (inklusive datorer som kör Nano Server och därmed inte har något annat gränssnitt). Kopiera filer genom att ange PSSession-ID: n som värdet för parametrarna New-FromSession och-ToSession, och Lägg till sökväg och-mål för att ange start Sök väg och mål. Till exempel Copy-item-Path c: \\myFile.txt-ToSession $s-destination d: \\ destinationFolder.
- Windows PowerShell-avskriften har förbättrats för att gälla alla värdbaserade program (till exempel Windows PowerShell ISE) förutom konsol värden (**powershell.exe**). Avskrifts alternativ (inklusive aktivering av systemomfattande avskrifter) kan konfigureras genom att aktivera inställningen **Aktivera PowerShell-Avskrifts** Grupprincip, som finns i administrativa mallar/Windows-komponenter/Windows PowerShell.
- Med en ny detaljerad skript spårnings funktion kan du aktivera detaljerad spårning och analys av skript användningen i Windows PowerShell på ett system. När du har aktiverat detaljerad skript spårning loggar Windows PowerShell alla skript block till händelse loggen ETW (Event Tracing for Windows) (ETW), **Microsoft-Windows-PowerShell/Operational**.
- Från och med Windows PowerShell 5,0 stöder nya cmdletar för kryptografisk meddelandesyntax kryptering och dekryptering av innehåll med hjälp av IETF-standardformat för kryptering av meddelanden som dokumenteras av [RFC5652](https://tools.ietf.org/html/rfc5652). Cmdletarna get-CmsMessage, Protect-CmsMessage och Unprotect-CmsMessage har lagts till i [Microsoft. PowerShell. Security](/powershell/module/Microsoft.PowerShell.Security) -modulen.
- Nya cmdlets i [Microsoft. PowerShell. Utility](/powershell/module/Microsoft.PowerShell.Utility) -modulen, get-körnings utrymme, debug-körnings utrymme, get-RunspaceDebug, Enable-RunspaceDebug och Disable-RunspaceDebug, gör att du kan ange fel söknings alternativ på en körnings utrymme och starta och stoppa fel sökning på en körnings utrymme. För fel sökning av godtyckliga körnings utrymmen (dvs. körnings utrymmen som inte är standard-körnings utrymme för en Windows PowerShell-konsol eller Windows PowerShell ISE session) kan du ange Bryt punkter i ett skript i Windows PowerShell och har lagt till Bryt punkter stoppa skriptet från att köras tills du kan koppla en fel sökare för att felsöka körnings utrymme-skriptet. Stöd för kapslad fel sökning för godtycklig körnings utrymmen har lagts till i Windows PowerShell-skript fel sökning för körnings utrymmen.
- En ny format-hex-cmdlet har lagts till i modulen [Microsoft. PowerShell. Utility](/powershell/module/Microsoft.PowerShell.Utility) .
  Med formatet-hex kan du Visa text data eller binära data i hexadecimalt format.
- Get-Urklipp och set-Clipboard-cmdletar har lagts till i [Microsoft. PowerShell. Utility](/powershell/module/Microsoft.PowerShell.Utility) -modulen. de fören klar överföringen av innehåll till och från en Windows PowerShell-session. Urklipps-cmdletarna stöder bilder, ljudfiler, fil listor och text.
- En ny cmdlet, Clear-RecycleBin, har lagts till i [Microsoft. PowerShell. Management](/powershell/module/Microsoft.PowerShell.Management) -modulen; den här cmdleten tömmer pappers korgen för en fast enhet, vilket inkluderar externa enheter. Som standard uppmanas du att bekräfta ett Clear-RecycleBin-kommando eftersom ConfirmImpact-egenskapen för cmdleten är inställd på ConfirmImpact. High.
- Med en ny cmdlet, New-TemporaryFile, kan du skapa en temporär fil som en del av skript. Som standard skapas den nya temporära filen i ```C:\Users\<user name>\AppData\Local\Temp``` .
- Cmdletarna Out-File, Add-Content och set-Contents har nu en New-NoNewline-parameter, som utelämnar en ny rad efter utdata.
- Cmdleten New-GUID utnyttjar .NET Framework GUID-klassen för att generera ett GUID, användbart när du skriver skript eller DSC-resurser.
- Eftersom fil versions information kan vara missvisande, särskilt när en fil har korrigerats, är nya FileVersionRaw-och ProductVersionRaw-skript egenskaper tillgängliga för FileInfo-objekt. Du kan till exempel köra följande kommando för att visa värdena för dessa egenskaper för powershell.exe, där $pid innehåller process-ID: t för en Windows PowerShell-session som körs: `Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force`
- Nya cmdlet: ar Enter-PSHostProcess och exit-PSHostProcess låter dig felsöka Windows PowerShell-skript i processer som är åtskilda från den aktuella processen som körs i Windows PowerShell-konsolen. Kör retur-PSHostProcess för att ange eller koppla till ett särskilt process-ID och kör sedan Get-körnings utrymme för att returnera den aktiva körnings utrymmen i processen. Kör Exit-PSHostProcess för att koppla från processen när du är färdig med att felsöka skriptet i processen.
- En ny cmdlet för wait-debugger har lagts till i modulen [Microsoft. PowerShell. Utility](/powershell/module/Microsoft.PowerShell.Utility) . Du kan köra wait-debugger för att stoppa ett skript i fel söknings programmet innan du kör nästa instruktion i skriptet.
- Fel söknings programmet för Windows PowerShell-arbetsflöde stöder nu kommando-eller TABB-slutförande och du kan felsöka kapslade arbets flödes funktioner. Nu kan du trycka på **CTRL + BREAK** för att ange fel sökaren i ett skript som körs, i både lokala och fjärranslutna sessioner, och i ett arbets flödes skript.
- En debug-Job-cmdlet har lagts till i [Microsoft. PowerShell. Core](/powershell/module/Microsoft.PowerShell.Core) -modulen för att felsöka körning av jobb skript för Windows PowerShell-arbetsflöde, bakgrund och jobb som körs i fjärrsessioner.
- Ett nytt tillstånd, AtBreakpoint, har lagts till för Windows PowerShell-jobb. AtBreakpoint-status gäller när ett jobb kör ett skript som innehåller angivna Bryt punkter och skriptet har nått en Bryt punkt. När ett jobb stoppas vid en fel söknings Bryt punkt måste du felsöka jobbet genom att köra cmdleten debug-Job.
- Windows PowerShell 5,0 implementerar stöd för flera versioner av en enda Windows PowerShell-modul i samma mapp i $PSModulePath. En RequiredVersion-egenskap har lagts till i ModuleSpecification-klassen för att hjälpa dig att få den önskade versionen av en modul. den här egenskapen kan inte anges samtidigt med egenskapen ModuleVersion. RequiredVersion stöds nu som en del av värdet för parametern FullyQualifiedName för cmdletarna get-module, import-module och Remove-module.
- Nu kan du utföra en modul versions validering genom att köra cmdleten test-ModuleManifest.
- Resultatet från cmdleten Get-Command visar nu en versions kolumn. en ny versions egenskap har lagts till i CommandInfo-klassen. Get-Command visar kommandon från flera versioner av samma modul. Egenskapen version är också en del av härledda klasser av CmdletInfo: CmdletInfo och ApplicationInfo.
- Get-Command har en ny parameter,-ShowCommandInfo, som returnerar ShowCommand-information som PSObjects. Detta är särskilt användbart för att visa-kommandot körs i Windows PowerShell ISE med hjälp av Windows PowerShell-fjärrkommunikation. Parametern-ShowCommandInfo ersätter den befintliga get-SerializedCommand-funktionen i modulen Microsoft. PowerShell. Utility, men get-SerializedCommand-skriptet är fortfarande tillgängligt för att stödja äldre skript.
- Med en ny cmdlet för Get-ItemPropertyValue kan du hämta värdet för en egenskap utan att använda punkt notation. I äldre versioner av Windows PowerShell kan du till exempel köra följande kommando för att hämta värdet för egenskapen Application base i register nyckeln PowerShellEngine: **(Get-ItemProperty-Path HKLM: \\ Software \\ Microsoft \\ PowerShell \\ 3 \\ PowerShellEngine-Name ApplicationBase). ApplicationBase**. Från och med Windows PowerShell 5,0 kan du köra **Get-ItemPropertyValue-Path HKLM: \\ Software \\ Microsoft \\ PowerShell \\ 3 \\ PowerShellEngine ApplicationBase**.
- I Windows PowerShell-konsolen används nu syntax för syntax, precis som i Windows PowerShell ISE.
- En ny NetworkSwitch-modul innehåller cmdletar som gör att du kan använda Switch, virtuellt LAN (VLAN) och grundläggande Layer 2 nätverks växel port konfiguration för Windows Server 2012 R2 logo typ-certifierade nätverks växlar.
- Parametern FullyQualifiedName har lagts till i cmdletarna import-module och Remove-module, för att stödja lagring av flera versioner av en enda modul.
- Spara – hjälp, uppdatera-hjälp, import-PSSession, export-PSSession och Get-Command har en ny parameter, FullyQualifiedModule, av typen ModuleSpecification. Lägg till den här parametern för att ange en modul med dess fullständigt kvalificerade namn.
- Värdet för **$PSVersionTable. PSVersion** har uppdaterats till 5,0.
- WMF 5,0 (PowerShell 5,0) inkluderar **pester** -modulen. Pester är ett ramverk för enhets testning för PowerShell. Det innehåller några enkla nyckelord som du kan använda för att skapa tester för dina skript.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nya funktioner i Windows PowerShell Desired State Configuration

- Med språk förbättringar för Windows PowerShell kan du definiera DSC-resurser (Desired State Configuration) för Windows PowerShell genom att använda klasser. Import-Dscresource Keyword Supports är nu ett faktiskt dynamiskt nyckelord; Windows PowerShell parsar den angivna modulens rotmapp, söker efter klasser som innehåller attributet Dscresource Keyword Supports. Du kan nu använda klasser för att definiera DSC-resurser där varken en MOF-fil eller en Dscresource Keyword Supports-undermapp i mappen module krävs. En fil med Windows PowerShell-moduler kan innehålla flera DSC-resurs klasser.
- En ny parameter, ThrottleLimit, har lagts till i följande cmdlets i PSDesiredStateConfiguration-modulen. Lägg till parametern ThrottleLimit för att ange antalet mål datorer eller enheter som du vill att kommandot ska fungera på samtidigt.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Jämför-DscConfiguration
  - Publicera – DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Uppdatera – DscConfiguration
- Med centraliserad DSC-fel rapportering loggas inte utförlig fel information i händelse loggen, men den kan skickas till en central plats för senare analys. Du kan använda den här centrala platsen för att lagra DSC-konfigurations fel som har inträffat för en server i miljön. När rapport servern har definierats i meta-konfigurationen skickas alla fel till rapport servern och lagras sedan i en databas. Du kan ställa in den här funktionen oavsett om en målnod är konfigurerad att hämta konfigurationer från en pull-server.
- Förbättringar för Windows PowerShell ISE enkel DSC-gruppredigering. Nu kan du göra följande.
  - Visa alla DSC-resurser i ett **konfigurations** -eller **Node** -block genom att ange **CTRL + blank steg** på en tom rad i blocket.
  - Automatisk komplettering av resurs egenskaper för **uppräknings** typen.
  - Automatisk komplettering av egenskapen **DependsOn** för DSC-resurser, baserat på andra resurs instanser i konfigurationen.
  - Förbättrad ifyllning av resurs egenskaps värden.
- En användare kan nu köra en resurs under en angiven uppsättning autentiseringsuppgifter genom att lägga till attributet **PSDscRunAsCredential** i ett Node-block. Till exempel PSDscRunAsCredential = Get-Credential contoso \\ DscUser. Den här funktionen är användbar för att skapa konfigurationer som kör Windows Installer och installations program för körbara filer, åtkomst till registrerings data filen per användare eller utföra andra uppgifter utanför den aktuella användar kontexten.
- stöd för 32-bitars (x86-baserade) har lagts till för nyckelordet **Configuration** .
- Windows PowerShell har nu stöd för anpassad hjälp för DSC-konfigurationer, som definieras genom att lägga till \[ CmdletBinding ()] i den genererade konfigurations funktionen.
- Ett nytt **DscLocalConfigurationManager** -attribut är ett konfigurations block som en meta-konfiguration, som används för att konfigurera den lokala DSC-Configuration Manager. Det här attributet begränsar en konfiguration som bara innehåller objekt som konfigurerar den lokala DSC-Configuration Manager. Under bearbetningen genererar den här konfigurationen en \* . meta. MOF-fil som sedan skickas till lämpliga målnod genom att köra cmdleten Set-DscLocalConfigurationManager.
- Partiella konfigurationer tillåts nu i Windows PowerShell 5,0. Du kan leverera konfigurations dokument till en nod i fragment. För att en nod ska kunna ta emot flera fragment av ett konfigurations dokument måste nodens lokala Configuration Manager först vara inställd för att ange förväntade fragment
- Synkronisering mellan datorer är ny i DSC i Windows PowerShell 5,0. Genom att använda de inbyggda WaitFor- \* resurserna (**WaitForAll**, **WaitForAny**och **WaitForSome**) kan du nu ange beroenden mellan datorer under konfigurations körningar, utan externa dirigeringar. Dessa resurser tillhandahåller synkronisering av nod till nod med hjälp av CIM-anslutningar över WS-man-protokollet.
  En konfiguration kan vänta på att en annan dators speciella resurs tillstånd ändras.
- Bara tillräckligt med administration (JEA), en ny säkerhetsfunktion för delegering, utnyttjar DSC och Windows PowerShell-begränsade körnings utrymmen för att skydda företag mot data förlust eller kompromissa med anställda, oavsett om de är avsiktliga eller oavsiktliga. Mer information om JEA, inklusive var du kan hämta xJEA DSC-resursen finns i [tillräckligt med administration](/powershell/scripting/learn/remoting/jea/overview).
- Följande nya cmdletar har lagts till i PSDesiredStateConfiguration-modulen.
  - En ny get-DscConfigurationStatus-cmdlet hämtar information på hög nivå om konfigurations status från en målnod. Du kan hämta status för senaste eller alla konfigurationer.
  - En ny compare-DscConfiguration-cmdlet jämför en angiven konfiguration med det aktuella läget för en eller flera målnod.
  - En ny cmdlet för publicerings-DscConfiguration kopierar en MOF-fil för konfiguration till en målnod, men tillämpar inte konfigurationen. Konfigurationen används vid nästa konsekvens steg, eller när du kör cmdleten Update-DscConfiguration.
  - Med en ny test-DscConfiguration-cmdlet kan du kontrol lera att en resulterande konfiguration matchar önskad konfiguration, returnerar antingen sant om konfigurationen matchar önskad konfiguration eller falskt om den faktiska konfigurationen inte matchar önskad konfiguration.
  - En ny Update-DscConfiguration-cmdlet tvingar fram en konfiguration som ska bearbetas. Om den lokala Configuration Manager är i pull-läge hämtar cmdleten konfigurationen från hämtnings servern innan den tillämpas.

### <a name="new-features-in-windows-powershell-ise"></a>Nya funktioner i Windows PowerShell ISE

- Nu kan du redigera Windows PowerShell-skript och-filer i en lokal kopia av Windows PowerShell ISE genom att köra Enter-PSSession för att starta en fjärrsession på datorn som lagrar de filer som du vill redigera och sedan köra **PSEdit \<path and file name on the remote computer\> **. Den här funktionen underlättar redigering av Windows PowerShell-filer som är lagrade på installations alternativet Server Core för Windows Server, där Windows PowerShell ISE inte kan köras.
- Cmdleten Start-avskrift stöds nu i Windows PowerShell ISE.
- Du kan nu felsöka fjärrskript i Windows PowerShell ISE.
- Ett nytt meny kommando, **Bryt alla** (Ctrl + B), slutar i fel söknings programmet för både lokala och fjärranslutna skript.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nya funktioner i Windows PowerShell-webbtjänster (hantering OData IIS-tillägg)

- Från och med Windows PowerShell 5,0 kan du generera en uppsättning Windows PowerShell-cmdlets baserat på de funktioner som exponeras av en angiven OData-slutpunkt, genom att köra cmdleten export-ODataEndpointProxy, som finns i den nya [Microsoft. PowerShell. OdataUtils](/powershell/module/microsoft.powershell.odatautils) -modulen.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Viktiga fel korrigeringar i Windows PowerShell 5,0

- Windows PowerShell 5,0 innehåller en ny COM-implementering som ger betydande prestanda förbättringar när du arbetar med COM-objekt. En demonstration av effekterna finns i [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Betydande prestanda förbättringar har gjorts för den första inläsningen av en Windows PowerShell-session, vilket förkortar TABB-tiden med nästan 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nya funktioner i Windows PowerShell 4,0

Windows PowerShell 4,0 är bakåtkompatibelt. Cmdlets, providers, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 3,0 och Windows PowerShell 2,0 fungerar i Windows PowerShell 4,0 utan ändringar.

Windows PowerShell 4,0 installeras som standard på Windows 8,1 och Windows Server 2012 R2. Installera Windows PowerShell 4,0 på Windows 7 med SP1 eller Windows Server 2008 R2 genom att ladda ned och installera [Windows Management Framework 4,0](https://www.microsoft.com/download/details.aspx?id=40855). Se till att läsa informationen om hämtningen och uppfyller alla system krav innan du installerar Windows Management Framework 4,0.

- [Nya funktioner i Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nya funktioner i Windows PowerShell ISE (Integrated Scripting Environment)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nya funktioner i Windows PowerShell-arbetsflöde](#new-features-in-windows-powershell-workflow)
- [Nya funktioner i Windows PowerShell-webbtjänster](#new-features-in-windows-powershell-web-services)
- [Nya funktioner i Windows PowerShell-Webbåtkomst](#new-features-in-windows-powershell-web-access)
- [Viktiga fel korrigeringar i Windows PowerShell 4,0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4,0 innehåller följande nya funktioner.

### <a name="new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Nya funktioner i Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) är ett nytt hanterings system i Windows PowerShell 4,0 som möjliggör distribution och hantering av konfigurations data för program varu tjänster och miljön där tjänsterna körs. Mer information om DSC finns i [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/getting-started/wingettingstarted).
- **Spara – hjälp** nu låter dig spara hjälp för moduler som är installerade på fjärrdatorer. Du kan använda Spara-hjälp för att ladda ned hjälp om modulen från en Internet-ansluten klient (där inte alla moduler som du vill ha hjälp om är installerade) och sedan kopiera den sparade hjälpen till en delad fjärrmapp eller en fjärrdator som inte har Internet åtkomst.
- Windows PowerShell-felsökaren har förbättrats för att tillåta fel sökning av Windows PowerShell-arbetsflöden, samt skript som körs på fjärrdatorer. Windows PowerShell-arbetsflöden kan nu felsökas på skript nivå från antingen Windows PowerShell-kommandoraden eller Windows PowerShell ISE. Windows PowerShell-skript, inklusive skript arbets flöden, kan nu felsökas via fjärrsessioner. Fjärrfelsökning bevaras över Windows PowerShell-fjärrsessioner som kopplas från och sedan återansluts senare.
- En **RunNow** -parameter för **register-ScheduledJob** och **set-ScheduledJob** eliminerar behovet av att ange ett omedelbart start datum och en tid för jobb med hjälp av parametern **trigger** .
- **Invoke-RestMethod** och **Invoke-WebRequest** låter dig nu ange alla huvuden med hjälp av parametern headers. Även om den här parametern alltid fanns, var den en av flera parametrar för webb-cmdlet: arna som resulterade i undantag eller fel.
- **Get-module** har en ny parameter, **FullyQualifiedName**, av typen **ModuleSpecification \[ ]**. Med parametern **FullyQualifiedName** för Get-module kan du nu ange en modul med hjälp av modulens namn, version och eventuellt GUID.
- Standard körnings princip inställningen på Windows Server 2012 R2 är **RemoteSigned**. I Windows 8,1 sker ingen ändring i standardinställningen.
- Från och med Windows PowerShell 4,0 stöds metod anrop med hjälp av dynamiska metod namn.
  Du kan använda en variabel för att lagra ett metod namn och sedan anropa metoden dynamiskt genom att anropa variabeln.
- Asynkrona arbets flödes jobb tas inte längre bort när tids gräns perioden som anges av den gemensamma parametern **PSElapsedTimeoutSec** Workflow har förflutit.
- En ny parameter, **RepeatIndefinitely**, har lagts till i cmdletarna **New-JobTrigger** och **set-JobTrigger** . Detta eliminerar behovet av att ange ett **TimeSpan. MaxValue** -värde för parametern **RepetitionDuration** för att köra ett schemalagt jobb upprepade gånger för en obestämd period.
- En **Passthru** -parameter har lagts till i cmdletarna **Enable-JobTrigger** och **disable-JobTrigger** . Parametern Passthru visar alla objekt som har skapats eller ändrats av ditt kommando.
- Parameter namnen för att ange en arbets grupp i cmdletarna **Add-Computer** och **Remove-Computer** är nu konsekventa. Båda cmdletarna använder nu parametern **WorkgroupName**.
- En ny gemensam parameter, **PipelineVariable**, har lagts till. Med PipelineVariable kan du spara resultatet av ett skickas-kommando (eller en del av ett skickas-kommando) som en variabel som kan skickas genom resten av pipelinen.
- Samlings filtrering med hjälp av Method-syntax stöds nu. Det innebär att du nu kan filtrera en samling objekt med hjälp av förenklad syntax, ungefär som för WHERE () eller Where-Object, formaterat som ett metod anrop. Följande är ett exempel: (Get-process). där ({$ _. Namn matchning ' PowerShell '})
- Cmdleten **Get-process** har en ny växel parameter, **IncludeUserName**.
- En ny cmdlet, **Get-FileHash**, som returnerar en filhash i ett av flera format för en angiven fil har lagts till.
- Om en modul i Windows PowerShell 4,0 använder **DefaultCommandPrefix** -nyckeln i manifestet, eller om användaren importerar en modul med parametern **prefix** , Visar egenskapen **ExportedCommands** för modulen kommandona i modulen med prefixet. När du kör kommandona med hjälp av module-kvalificerad syntax, Modulnamn \\ commandname, måste kommando namnen innehålla prefixet.
- Värdet för **$PSVersionTable. PSVersion** har uppdaterats till 4,0.
- **WHERE ()-** operatorns beteende har ändrats. `Collection.Where('property -match name')` att acceptera ett sträng uttryck i formatet `"Property -CompareOperator Value"` stöds inte längre.
  Operatorn **WHERE ()** accepterar dock sträng uttryck i formatet för en script block; Detta stöds fortfarande.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nya funktioner i Windows PowerShell ISE (Integrated Scripting Environment)

- Windows PowerShell ISE stöder fel sökning av både Windows PowerShell-arbetsflöde och fjärrfelsökning av skript.
- IntelliSense-stöd har lagts till för Windows PowerShell Desired State Configuration providers och konfigurationer.

### <a name="new-features-in-windows-powershell-workflow"></a>Nya funktioner i Windows PowerShell-arbetsflöde

- Stöd har lagts till för en ny **PipelineVariable** common-parameter i kontexten för iterativa pipelines, till exempel de som används av System Center Orchestrator; det vill säga pipelines som kör kommandon som bara är från vänster till höger, i stället för att infogas direkt med hjälp av strömning.
- Parameter bindningen har förbättrats avsevärt för att fungera utanför scenarier med tabbar, till exempel med kommandon som inte finns i den aktuella körnings utrymme.
- Stöd för anpassade behållar aktiviteter har lagts till i Windows PowerShell-arbetsflöde. Om en aktivitets parameter är av typen **aktivitet**, **aktivitet \[ ]** (eller är en allmän samling aktiviteter) och användaren har angett ett skript block som argument, konverterar Windows PowerShell-arbetsflöde skript blocket till XAML, precis som med normalt Windows PowerShell skript-till-arbets flödes kompilering.
- Efter en krasch återansluter Windows PowerShell-arbetsflöde automatiskt till hanterade noder.
- Du kan nu begränsa **förgrunds-och parallella** aktivitets uttryck med hjälp av egenskapen **ThrottleLimit** .
- Den gemensamma parametern **ErrorAction** har ett nytt giltigt värde, **suspend**, som endast är för arbets flöden.
- En slut punkt för arbets flöde stängs nu automatiskt om det inte finns några aktiva sessioner, inga pågående jobb och inga väntande jobb. Den här funktionen bevarar resurser på datorn som fungerar som arbets flödes server när de automatiska stängnings villkoren har uppfyllts.

### <a name="new-features-in-windows-powershell-web-services"></a>Nya funktioner i Windows PowerShell-webbtjänster

- När ett fel uppstår i Windows PowerShell-webbtjänster (PSWS, kallas även OData IIS-tillägg för hantering) medan en cmdlet körs, returneras mer detaljerade fel meddelanden till anroparen. Dessutom följer fel koderna i [rikt linjerna för Windows Azure REST API fel kod](/rest/api/storageservices/Common-REST-API-Error-Codes).
- En slut punkt kan nu definiera API-versionen, samt framtvinga användningen av en speciell API-version. När versions matchningen sker mellan klienten och servern, visas felen för både klienten och servern.
- Hantering av sändnings schemat har förenklats genom att automatiskt generera värden för fält som saknas i schemat. Genereringen sker, som en användbar start punkt, även om sändnings schemat inte finns.
- Typ hantering i PSWS har förbättrats för att ge stöd åt typer som använder en annan konstruktor än Standardkonstruktorn, genom att fungera på samma sätt som **PSTypeConverter** i Windows PowerShell. På så sätt kan du använda komplexa typer med PSWS.
- PSWS tillåter nu att en associerad instans expanderas när en fråga körs. För större binära innehåll (till exempel bilder, ljud eller video) är överförings kostnaden betydande och det är bättre att överföra binära data utan kodning. PSWS använder namngivna resurs strömmar för överföring utan kodning.
  Den namngivna resurs data strömmen är en egenskap för en entitet av typen **EDM. Stream** . Varje namngiven resurs ström har en separat URI för GET-eller UPDATE-åtgärder.
- OData-åtgärder tillhandahåller nu en mekanism för att anropa icke-CRUD (skapa, läsa, uppdatera och ta bort) metoder på en resurs. Du kan anropa en åtgärd genom att skicka en HTTP POST-begäran till den URI som har definierats för åtgärden. Parametrarna för åtgärden definieras i bröd texten i POST-begäran.
- För att vara konsekvent med rikt linjerna i Windows Azure bör alla URL: er vara förenklade. En ändring som ingår i **nyckeln as-segment** tillåter att enskilda nycklar representeras som segment. Observera att referenser som använder flera nyckel värden kräver kommaavgränsade värden i parentetiska notation, som tidigare.
- Före den här versionen av PSWS var det enda sättet att utföra åtgärder för att skapa, uppdatera eller ta bort att anropa post, skicka eller ta bort på en resurs på den översta nivån. I den här versionen av PSWS, som innehåller resurs åtgärder, kan användarna få samma resultat samtidigt som den når samma resurs mindre direkt, vilket närmar sig om dessa resurser fanns.

### <a name="new-features-in-windows-powershell-web-access"></a>Nya funktioner i Windows PowerShell-Webbåtkomst

- Du kan koppla från och återansluta till befintliga sessioner i den webbaserade konsolen för webb åtkomst för Windows PowerShell. Med knappen **Spara** i den webbaserade konsolen kan du koppla från en session utan att ta bort den och återansluta till sessionen en annan gång.
- Standard parametrar kan visas på inloggnings sidan. Om du vill visa standard parametrar konfigurerar du värden för alla inställningar som visas i avsnittet **valfria anslutnings inställningar** på inloggnings sidan i en fil med namnet **web.config**. Du kan använda **web.config** -filen för att konfigurera alla valfria anslutnings inställningar förutom för en andra eller en annan uppsättning autentiseringsuppgifter.
- I Windows Server 2012 R2 kan du fjärrhantera auktoriseringsregler för Windows PowerShell-webbåtkomst. Cmdletarna **Add-PswaAuthorizationRule** och **test-PswaAuthorizationRule** innehåller nu en parameter för autentiseringsuppgifter som gör det möjligt för administratörer att hantera auktoriseringsregler från en fjärrdator eller i en Windows PowerShell-webbåtkomst-session.
- Nu kan du ha flera Windows PowerShell-webbåtkomster i en webbsession med en ny webb läsar flik för varje session. Du behöver inte längre öppna en ny webbläsarsession för att ansluta till en ny session i den webbaserade Windows PowerShell-konsolen.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Viktiga fel korrigeringar i Windows PowerShell 4,0

- **Get-Counter** kan nu returnera räknare som innehåller ett apostrof-tecken i franska versioner av Windows.
- Nu kan du Visa **gettype** -metoden för avserialiserade objekt.
- **#Requires** -instruktioner låter användarna kräva administratörs behörighet, om det behövs.
- **Import-CSV-** cmdleten ignorerar nu tomma rader.
- Ett problem där Windows PowerShell ISE använder för mycket minne när du kör kommandot **Invoke-WebRequest** har åtgärd ATS.
- **Get-module** visar nu modul versioner i en **versions** kolumn.
- Remove-item-rekursivt tar nu bort objekt från undermappar som förväntat.
- En **användar namns** egenskap har lagts till för att hämta utdata för **process** objekt.
- Cmdleten **Invoke-RestMethod** returnerar nu alla tillgängliga resultat.
- **Lägg till medlem** börjar nu gälla på hash, även om hash ännu inte har öppnats.
- **Select-Object-Expand** fungerar inte längre eller genererar ett undantag om egenskapens värde är null eller tomt.
- **Get-process** kan nu användas i en pipeline med andra kommandon som hämtar egenskapen **computername** från objekt.
- **ConvertTo-JSON** och **ConvertFrom-JSON** kan nu acceptera termer inom dubbla citat tecken, och dess fel meddelanden kan nu lokaliseras.
- **Get-Job** returnerar nu alla slutförda schemalagda jobb, även i nya sessioner.
- Problem med att montera och demontera virtuella hård diskar med hjälp av **fil Systems** leverantören i Windows PowerShell 4,0 har åtgärd ATS. Windows PowerShell kan nu identifiera nya enheter när de monteras i samma session.
- Du behöver inte längre läsa in **ScheduledJob** -eller **Workflow** -moduler för att arbeta med sina jobb typer.
- Prestanda förbättringar har gjorts i processen för att importera arbets flöden som definierar kapslade arbets flöden. den här processen är nu snabbare.

## <a name="new-features-in-windows-powershell-30"></a>Nya funktioner i Windows PowerShell 3,0

Windows PowerShell 3,0 innehåller följande nya funktioner.

- [Windows PowerShell-arbetsflöde](#windows-powershell-workflow)
- [Windows PowerShell-Webbåtkomst](#windows-powershell-web-access)
- [Nya Windows PowerShell ISE funktioner](#new-windows-powershell-ise-features)
- [Stöd för Microsoft .NET Framework 4,0](#support-for-microsoft-net-framework-4)
- [Stöd för Windows Preinstallation Environment](#support-for-windows-preinstallation-environment)
- [Frånkopplade sessioner](#disconnected-sessions)
- [Robust session-anslutning](#robust-session-connectivity)
- [Uppdaterings Bart hjälp system](#updatable-help-system)
- [Utökad onlinehjälp](#enhanced-online-help)
- [CIM-integrering](#cim-integration)
- [Konfigurationsfiler för session](#session-configuration-files)
- [Schemalagda jobb och Schemaläggaren-integrering](#scheduled-jobs-and-task-scheduler-integration)
- [Språk förbättringar för Windows PowerShell](#windows-powershell-language-enhancements)
- [Nya Core-cmdletar](#new-core-cmdlets)
- [Förbättringar av befintliga kärn-cmdlets och providers](#improvements-to-existing-core-cmdlets-and-providers)
- [Import och identifiering av fjärrmodul](#remote-module-import-and-discovery)
- [Förbättrad ifyllning av flikar](#enhanced-tab-completion)
- [Automatisk inläsning av modul](#module-auto-loading)
- [Förbättringar i modul upplevelse](#module-experience-improvements)
- [Förenklad kommando identifiering](#simplified-command-discovery)
- [Förbättrad loggning, diagnostik och grupprincip support](#improved-logging-diagnostics-and-group-policy-support)
- [Förbättringar av formatering och utdata](#formatting-and-output-improvements)
- [Förbättrad konsol värd upplevelse](#enhanced-console-host-experience)
- [Ny cmdlet och värdbaserade API: er](#new-cmdlet-and-hosting-apis)
- [Prestandaförbättringar](#performance-improvements)
- [Stöd för RunAs och delad värd](#runas-and-shared-host-support)
- [Förbättringar av Special Character-hantering](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell-arbetsflöde

Windows PowerShell-arbetsflöde ger kraften i Windows Workflow Foundation till Windows PowerShell.
Du kan skriva arbets flöden i XAML eller på Windows PowerShell-språket och köra dem på samma sätt som du skulle köra en cmdlet. `Get-Command`Cmdleten hämtar arbets flödes kommandon och `Get-Help` cmdlet: en får hjälp för arbets flöden.

Arbets flöden är sekvenser av hanterings aktiviteter för datorer som är långvariga, upprepnings bara, frekventa, kan göras parallella, avbrotts bar, pausad och kan startas om. Arbets flöden kan återupptas från ett avsiktligt eller oavsiktligt avbrott, till exempel ett nätverks avbrott, en omstart av Windows eller ett strömavbrott.

Arbets flöden är också bärbara; de kan exporteras som eller importeras från XAML-filer. Du kan skriva anpassade sessionsinställningar som tillåter att arbets flöden eller aktiviteter i ett arbets flöde körs av delegerade eller underordnade användare.

Följande är fördelarna med Windows PowerShell-arbetsflöde

- Automatisering av sekvenserade, långvariga uppgifter.
- **Fjärrövervakning av tids krävande uppgifter**. Status och förlopp för aktiviteter visas när som helst.
- **Hantering av multidatorer.** Kör aktiviteter samtidigt som arbets flöden på hundratals hanterade noder.
  Windows PowerShell-arbetsflöde innehåller ett inbyggt bibliotek med vanliga hanterings parametrar, t. ex. **PSComputerName**, som möjliggör hantering av flera datorer.
- **Körning av komplexa processer för en aktivitet.** Du kan kombinera relaterade skript som implementerar ett helt scenario från slut punkt till slut punkt i ett enda arbets flöde.
- **Persistence.**: ett arbets flöde sparas (eller checkar pekas) vid vissa punkter som definieras av författaren så att du kan återuppta arbets flödet från den senaste sparade aktiviteten (eller kontroll punkten) i stället för att starta om arbets flödet från början.
- **Stabilitet.** Automatisk återställning av felen. Arbets flöden överleva planerade och oplanerade omstarter. Du kan pausa arbets flödes körningen och sedan återuppta arbets flödet från den senaste beständighets punkten.
  Arbets flödes författare kan ange att vissa aktiviteter ska köras på nytt om det skulle uppstå ett eller flera hanterade noder.
- **Möjlighet att koppla från, återansluta och köra i frånkopplade sessioner.** Användare kan ansluta och koppla från arbets flödes servern, men arbets flödet körs kontinuerligt. Du kan logga ut från klient datorn eller starta om klient datorn och övervaka arbets flödets körning från en annan dator utan att avbryta arbets flödet.
- **Tids.** Arbets flödes uppgifter kan schemaläggas som vilken Windows PowerShell-cmdlet eller skript som helst.
- **Begränsning av arbets flöde och anslutning.** Arbets flödes körning och anslutningar till noder kan begränsas, vilket möjliggör skalbarhet och scenarier med hög tillgänglighet.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access

Windows PowerShell-webbåtkomsten är en funktion i Windows Server 2012 som låter användarna köra Windows PowerShell-kommandon och-skript i en webbaserad konsol. Enheter som använder den webbaserade konsolen kräver inte Windows PowerShell, program vara för fjärrhantering eller plugin-program för webbläsare. Allt som krävs är en korrekt konfigurerad Gateway för Windows PowerShell-webbåtkomst och en klient enhets webbläsare som stöder Java Script och accepterar cookies.

Mer information finns i [distribuera Windows PowerShell-webbåtkomst](/previous-versions/powershell/scripting/components/web-access/install-and-use-windows-powershell-web-access).

### <a name="new-windows-powershell-ise-features"></a>Nya Windows PowerShell ISE funktioner

För Windows PowerShell 3,0 innehåller Windows PowerShell ISE (Integrated Scripting Environment) många nya funktioner, inklusive IntelliSense, show-Fönstret Kommando, ett enhetligt konsol fönster, kodfragment, klammerparenteser-matchning, expandera, minimera avsnitt, Spara automatiskt, senaste objekt lista, omfattande kopiering, block kopia och fullständig support för att skriva Windows PowerShell-skript arbets flöden. Mer information finns i [about_Windows_PowerShell_ISE](/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise).

### <a name="support-for-microsoft-net-framework-4"></a>Stöd för Microsoft .NET Framework 4

Windows PowerShell är konstruerat mot CLR (Common Language Runtime) 4,0. Användare av cmdlet, skript och arbets flöden kan använda de nya Microsoft .NET Framework 4-klasserna i Windows PowerShell, med funktioner som omfattar programkompatibilitet och distribution av program, Managed Extensibility Framework, parallell data behandling, nätverk, Windows Communication Foundation och Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Stöd för Windows Preinstallation Environment

Windows PowerShell 3,0 är en valfri komponent i Windows Preinstallation Environment (Windows PE) 4,0 för Windows 8. Windows PE är ett minimalt operativ system som startar en dator utan operativ system och förbereder den för Windows-installation. Windows PE kan användas för att partitionera och formatera hård diskar, Kopiera disk avbildningar till en dator och initiera Installationsprogrammet för Windows från en nätverks resurs.
Windows PowerShell 3,0 kan användas i Windows PE för att hantera distributions-, diagnostik-och återställnings scenarier.

### <a name="disconnected-sessions"></a>Frånkopplade sessioner

Från och med Windows PowerShell 3,0 sparas permanenta användar hanterade sessioner ("PSSessions") som du skapar med hjälp av cmdleten New-PSSession på fjärrdatorn. De är inte längre beroende av den session där de skapades.

Du kan nu koppla från en session utan att avbryta de kommandon som körs i sessionen. Du kan stänga sessionen och stänga av datorn. Senare kan du återansluta till sessionen från en annan session på samma eller på en annan dator.

Parametern **computername** för `Get-PSSession` cmdleten hämtar nu alla användares sessioner som ansluter till datorn, även om de startades i en annan session på en annan dator. Du kan ansluta till sessionerna, Hämta resultatet från kommandon, starta nya kommandon och sedan koppla från sessionen.

Nya cmdletar har lagts till för att stödja funktionen frånkopplade sessioner, inklusive `Disconnect-PSSession` , `Connect-PSSession` och `Receive-PSSession` , och nya parametrar har lagts till i cmdletar som hanterar PSSessions, till exempel parametern **InDisconnectedSession** för `Invoke-Command` cmdleten.

Funktionen frånkopplade sessioner stöds bara när datorerna på både den ursprungliga ("klienten") och avslutande ("Server") slutar på anslutningen kör Windows PowerShell 3,0.

### <a name="robust-session-connectivity"></a>Robust session-anslutning

Windows PowerShell 3,0 upptäcker oväntade förluster av anslutningen mellan klienten och servern och försöker återupprätta anslutningen och återuppta körningen automatiskt. Om klient-/server anslutningen inte kan återupprättas inom den tilldelade tiden, meddelas användaren och sessionen kopplas från. Under försöket att återansluta tillhandahåller Windows PowerShell kontinuerlig feedback till användaren.

Om den frånkopplade sessionen startades med hjälp av InvokeCommand, skapar Windows PowerShell ett jobb för den frånkopplade sessionen för att göra det enklare att återansluta och återuppta körningen.

Dessa funktioner ger en mer tillförlitlig och rekonstruerbar fjärr kommunikations upplevelse och gör det möjligt för användare att utföra långvariga uppgifter som kräver robusta sessioner, till exempel arbets flöden.

### <a name="updatable-help-system"></a>Uppdaterings Bart hjälp system

Nu kan du hämta uppdaterade hjälpfiler för cmdletarna i dina moduler. `Update-Help`Cmdleten identifierar de senaste hjälpfilerna, laddar ned dem från Internet, packar upp dem, validerar dem och installerar dem i rätt språkspecifik katalog för modulen.

Om du vill använda de uppdaterade hjälpfilerna skriver du bara `Get-Help` . Du behöver inte starta om Windows eller Windows PowerShell. Om du vill uppdatera hjälpen för moduler i $pshome-katalogen startar du Windows PowerShell med alternativet "kör som administratör".

För att stödja användare som inte har Internet åtkomst och användare bakom brand väggar laddar den nya `Save-Help` cmdleten ned hjälpfiler till en fil system katalog, till exempel en fil resurs. Användare kan sedan använda `Update-Help` cmdleten för att hämta uppdaterade hjälpfiler från fil resursen.

Du kan använda `Update-Help` cmdleten för att uppdatera hjälpfiler för alla eller vissa moduler i alla användar gränssnitts kulturer som stöds. Du kan även skicka ett `Update-Help` kommando i din Windows PowerShell-profil.
Som standard laddar Windows PowerShell ned hjälpfilerna för en modul högst en gång varje dag.

Windows 8-och Windows Server 2012-moduler innehåller inte hjälpfiler. Om du vill hämta de senaste hjälpfilerna skriver du `Update-Help` . Mer information får du genom `Get-Help` att skriva (utan parametrar) eller se [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_Updatable_Help).

Om hjälpfilerna för en cmdlet inte är installerade på datorn `Get-Help` visar cmdleten nu den automatiskt genererade hjälpen. Den automatiskt genererade hjälpen innehåller kommandosyntaxen och instruktioner för `Update-Help` att använda cmdleten för att hämta hjälpfiler.

Alla modulblad kan stödja uppdaterings bar hjälp för sin modul. Du kan inkludera hjälpfiler i modulen och använda uppdaterings bara hjälp för att uppdatera dem eller utelämna hjälpfilerna och använda uppdaterbar hjälp för att installera dem. Mer information om stöd för uppdaterings bara hjälp finns i [support uppdaterings bara hjälp](/powershell/scripting/developer/module/supporting-updatable-help).

### <a name="enhanced-online-help"></a>Utökad onlinehjälp

Onlinehjälpen för Windows PowerShell är en värdefull resurs för alla användare, men det är särskilt viktigt för användare som inte kan installera uppdaterade hjälpfiler.

Om du vill ha Onlinehjälp för en Windows PowerShell-cmdlet skriver du:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell öppnar online-versionen av hjälp avsnittet i din standard webbläsare.

Funktionen **Get-Help-online** i Windows PowerShell 3,0 är nu ännu kraftfull eftersom den fungerar även om hjälpfilerna för cmdlet: en inte är installerade på datorn. Funktionen **Get-Help-online** hämtar hjälp avsnittet URI för online från egenskapen HelpUri för cmdletar och avancerade funktioner.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
https://go.microsoft.com/fwlink/?LinkID=223923
```

Från och med Windows PowerShell 3,0 kan författare av C#-cmdletar fylla i egenskapen **HelpUri** genom att skapa ett **HelpUri** -attribut i cmdlet-klassen. Författare av avancerade funktioner kan definiera en **HelpUri** -egenskap för attributet **CmdletBinding** . Värdet för egenskapen **HelpUri** måste börja med http eller https.

Du kan också inkludera ett **HelpUri** -värde i den första relaterade länken i en XML-baserad cmdlet-hjälpfil eller. Länk direktiv för kommenterings-baserad hjälp i en funktion.

Mer information om support online finns i [support online](/powershell/scripting/developer/module/supporting-online-help) i Microsoft docs.

### <a name="cim-integration"></a>CIM-integrering

Windows PowerShell 3,0 innehåller stöd för Common Information Model (CIM), som innehåller gemensamma definitioner av hanterings information för system, nätverk, program och tjänster, så att de kan utbyta hanterings information mellan heterogena system. Stöd för CIM i Windows PowerShell 3,0, inklusive möjligheten att skapa Windows PowerShell-cmdletar baserade på nya eller befintliga CIM-klasser, kommandon baserade på XML-filer för cmdlet-definition, stöd för CIM-.NET Framework. API, CIM Management-cmdletar och WMI 2,0-leverantörer.

### <a name="session-configuration-files"></a>Konfigurationsfiler för session

Från och med Windows PowerShell 3,0 kan du utforma en anpassad sessionsinformation genom att använda en fil.
Med den nya konfigurations filen för sessionen kan du fastställa miljön för sessioner som använder-konfigurationen, inklusive vilka moduler, skript och format filer som läses in i sessioner, vilka cmdletar och språk element som användare kan använda, vilka moduler och skript de kan köra och vilka variabler de kan se.

Du kan utforma en session där användare bara kan köra cmdletar från en viss modul, eller en session där användare har fullständigt språk, åtkomst till alla moduler och åtkomst till skript som utför avancerade uppgifter.

I tidigare versioner av Windows PowerShell var kontroll på den här nivån bara tillgänglig för de som kan skriva ett C#-program eller ett komplext start skript. Nu kan alla medlemmar i gruppen Administratörer på datorn anpassa en sessions konfiguration med hjälp av en konfigurations fil.

Använd cmdleten om du vill skapa en konfigurations fil för sessionen `New-PSSessionConfigurationFile` . Använd `Register-PSSessionConfiguration` cmdletarna or set-PSSessionConfiguration för att tillämpa sessionens konfigurations fil på en konfiguration av sessionen.

Mer information finns i [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files) och `New-PSSessionConfigurationFile` .

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Schemalagda jobb och Schemaläggaren-integrering

Nu kan du schemalägga bakgrunds jobb i Windows PowerShell och hantera dem i Windows PowerShell och i Schemaläggaren.

Schemalagda Windows PowerShell-jobb är en användbar hybrid av Windows PowerShell-arbetsjobb och Schemaläggaren-aktiviteter.

Som Windows PowerShell bakgrunds jobb körs schemalagda jobb asynkront i bakgrunden.
Instanser av schemalagda jobb som har slutförts kan hanteras med hjälp av jobb-cmdletar, till exempel `Start-Job` och `Get-Job` .

Precis som aktiviteter i Schemaläggaren kan du köra schemalagda jobb vid ett engångs-eller reaktuellt schema, eller som svar på en åtgärd eller händelse. Du kan visa och hantera schemalagda jobb i Schemaläggaren, aktivera och inaktivera dem efter behov, köra dem eller använda dem som mallar och ange under vilka omständigheter jobben ska starta.

Dessutom levereras schemalagda jobb med en anpassad uppsättning cmdlets för att hantera dem. Med cmdletarna kan du skapa, redigera, hantera, inaktivera och återaktivera schemalagda jobb, skapa schemalagda jobb utlösare och ange alternativ för schemalagda jobb.

Mer information om schemalagda jobb finns [about_Scheduled_Jobs](/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1).

### <a name="windows-powershell-language-enhancements"></a>Språk förbättringar för Windows PowerShell

Windows PowerShell 3,0 innehåller många funktioner som är utformade för att göra språket enklare, enklare att använda och för att undvika vanliga fel. Förbättringarna inkluderar egenskaper för egenskaps uppräkning, antal och längd på skalära objekt, nya omdirigerings-operatörer, $Using omfångs modifierare, PSItem automatisk variabel, flexibel teckenformatering, attribut för variabler, förenklade attributargument, numeriska kommando namn, stoppa-parsing-operatorn, förbättrad array-ihopbuntning, nya bit operatörer, beställda ord listor, PSCustomObject-dataflöde och förbättrad

### <a name="new-core-cmdlets"></a>Nya Core-cmdletar

Nya cmdletar har lagts till i Windows PowerShell Core-installationen, inklusive cmdlet: ar för att hantera schemalagda jobb, frånkopplade sessioner, CIM-integrering och det uppdaterings bara hjälp systemet.

- CimCmdlets
  - Get-CimAssociatedInstance
  - Get-CimClass
  - Get-CimInstance
  - Get-CimSession
  - Invoke-CimMethod
  - New-CimInstance
  - New-CimSession
  - New-CimSessionOption
  - Registrera – CimIndicationEvent
  - Remove-CimInstance
  - Remove-CimSession
  - Set-CimInstance
- Microsoft. PowerShell. Core
  - Anslut – PSSession
  - Koppla från-PSSession
  - New-PSSessionConfigurationFile
  - New-PSTransportOption
  - Ta emot – PSSession
  - Återuppta – jobb
  - Spara – hjälp
  - Pausa – jobb
  - Test-PSSessionConfigurationFile
  - Uppdatera – hjälp
- Microsoft. PowerShell. Diagnostics
  - New-WinEvent
- Microsoft. PowerShell. Management
  - Get-ControlPanelItem
  - Byt namn – dator
  - Visa ControlPanelItem
- Microsoft.PowerShell.Utility
  - ConvertFrom – JSON
  - ConvertTo-Json
  - Get-TypeData
  - Invoke-RestMethod
  - Anropa-webbegäran
  - Remove-TypeData
  - Visa-kommando
  - Avblockera – fil
- PSScheduledJob
  - Add-JobTrigger
  - Disable-JobTrigger
  - Disable-ScheduledJob
  - Aktivera – JobTrigger
  - Aktivera – ScheduledJob
  - Get-JobTrigger
  - Get-ScheduledJob
  - Get-ScheduledJobOption
  - New-JobTrigger
  - New-ScheduledJobOption
  - Registrera – ScheduledJob
  - Set-JobTrigger
  - Set-ScheduledJob
  - Set-ScheduledJobOption
  - Avregistrera-ScheduledJob
- PSWorkflow
  - New-PSWorkflowExecutionOption
  - New-PSWorkflowSession
- PSWorkflowUtility
  - Invoke-arbetsflöde
- ISE
  - Get-IseSnippet
  - Importera – IseSnippet
  - New-IseSnippet

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Förbättringar av befintliga kärn-cmdlets och providers

Windows PowerShell 3,0 innehåller nya funktioner för befintliga cmdlets, inklusive den förenklade syntaxen, och nya parametrar för följande cmdlet: Computer-cmdletar, CSV-cmdletar, get-ChildItem, Get-Command, get-Content, get-historik, Measure-Object, Security-cmdletar, Select-Object, Select-String, Split-Path, start process, tee-Object, Test-Connection, Add-member och WMI-cmdletar.

Windows PowerShell-providers har också förbättrats avsevärt, inklusive stöd för certifikat leverantörer för hantering av SSL-certifikat (Secure Socket Layer) för webb värd, stöd för autentiseringsuppgift, beständiga nätverks enheter och alternativa data strömmar i fil system enheter.

### <a name="remote-module-import-and-discovery"></a>Import och identifiering av fjärrmodul

Windows PowerShell 3,0 utökar modulen identifiering, import och implicita fjärr kommunikations funktioner på fjärrdatorer. Cmdleten för modulen hämtar moduler på fjärrdatorer och importerar modulerna till en fjärrdator eller en lokal dator med hjälp av Windows PowerShell-fjärrkommunikation. Med det nya stödet för CIM-session kan du använda CIM och WMI för att hantera datorer som inte är Windows-datorer genom att importera kommandon till den lokala datorn som körs implicit på fjärrdatorn.

Mer information finns i hjälp avsnitten för `Get-Module` `Import-Module` cmdletarna och.

### <a name="enhanced-tab-completion"></a>Förbättrad ifyllning av flikar

Med tabbtangenten i Windows PowerShell-konsolen slutförs nu namn på cmdlets, parametrar, parameter värden, uppräkningar, .NET Framework-typer, COM-objekt, dolda kataloger med mera.
Funktionen för slut för ande av flikar skrivs helt om baserat på en ny parser och en abstrakt syntax för att stödja fler scenarier, inklusive InMemory-tolknings träd och fliken mitt linje slut.

### <a name="module-auto-loading"></a>Automatisk inläsning av modul

`Get-Command`Cmdleten hämtar nu alla cmdletar och funktioner från alla moduler som är installerade på datorn, även om modulen inte har importer ATS till den aktuella sessionen.

När du hämtar den cmdlet som du behöver kan du använda den direkt utan att importera några moduler.
Windows PowerShell-moduler importeras nu automatiskt när du använder valfri cmdlet i modulen. Du behöver inte längre söka efter modulen och importera den för att använda dess cmdlets.

Automatisk import av moduler utlöses med hjälp av cmdleten i ett kommando, som körs `Get-Command` för en cmdlet utan jokertecken eller `Get-Help` som körs för en cmdlet utan jokertecken.

Du kan aktivera, inaktivera och konfigurera automatisk import av moduler med hjälp av **$PSModuleAutoLoadingPreference** Preference-variabeln.

Mer information finns i [about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules), [about_Preference_Variables](/powershell/module/microsoft.powershell.core/about/about_Preference_Variables)och hjälp avsnitten för `Get-Command` `Import-Module` cmdletarna och.

### <a name="module-experience-improvements"></a>Förbättringar i modul upplevelse

Windows PowerShell 3,0 ger avancerad funktions support för moduler, inklusive följande nya funktioner.

1. Modul loggning för enskilda moduler (LogPipelineExecutionDetails) och den nya inställningen "Aktivera loggning av modul" grupprincip
2. Utökade modul objekt som visar värdena från modulens manifest
3. Ny **ExportedCommands** -egenskap för moduler, inklusive kapslade moduler, som kombinerar kommandon av alla typer
4. Förbättrad identifiering av tillgängliga (ej importerade) moduler, inklusive att tillåta **Path** -och **ListAvailable** -parametrar i samma kommando
5. Ny **DefaultCommandPrefix** -nyckel i modul manifest som undviker namn konflikter utan att ändra kod i modulen.
6. Förbättrade modul krav, inklusive fullt kvalificerade nödvändiga moduler med version och GUID och automatisk import av nödvändiga moduler
7. Tystare, effektiv drift av `New-ModuleManifest` cmdleten.
8. Ny **modul** -parameter för #Requires
9. Förbättrad `Import-Module` cmdlet med både **MinimumVersion** -och **RequiredVersion** -parametrar.

### <a name="simplified-command-discovery"></a>Förenklad kommando identifiering

Du behöver inte längre importera alla moduler för att identifiera de kommandon som är tillgängliga för din session. I Windows PowerShell 3,0 `Get-Command` hämtar cmdleten alla kommandon från alla installerade moduler. Om du använder ett kommando importeras modulen som exporterar kommandot automatiskt till sessionen.

Den nya `Show-Command` cmdleten är särskilt utformad för nybörjare. Du kan söka efter kommandon i ett fönster. Du kan visa alla kommandon eller filtrera efter modul, importera en modul genom att klicka på en knapp, använda text rutor och list rutor för att skapa ett giltigt kommando och sedan kopiera eller köra kommandot utan att behöva lämna fönstret.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Förbättrad loggning, diagnostik och grupprincip support

Windows PowerShell 3,0 förbättrar loggnings-och spårnings stödet för kommandon och moduler med stöd för händelse spårning i Windows-loggar (ETW), en redigerbar **LogPipelineExecutionDetails** -egenskap för moduler och grupprincip inställningen "Aktivera loggning av modul". Du kan nu hämta parameter värden från logg information genom att Visa logg egenskaper.

### <a name="formatting-and-output-improvements"></a>Förbättringar av formatering och utdata

Nya förbättringar av formatering och utdata förbättrar effektiviteten hos alla Windows PowerShell-användare. Förbättringarna är bland annat omdirigering av utdata för alla strömmar, en utökad cmdlet för uppdaterings typ som lägger till typer dynamiskt utan Format.ps1XML-filer, automatiskt radbyte i utdata, standardformat för formatering av anpassade objekt, **PSCustomObject** -typ, förbättrad formatering för WMI-objekt och heterogena objekt, samt stöd för identifiering av metod överlagringar.

### <a name="enhanced-console-host-experience"></a>Förbättrad konsol värd upplevelse

Windows PowerShell-konsolens värd program har nya funktioner i Windows PowerShell 3,0, inklusive en enkel trådad inne slutning som standard. Alternativet för att köra med PowerShell i Utforskaren gör att du kan köra skript i en obegränsad session genom att högerklicka. Ny konsol värd start logik startar Windows PowerShell snabbare och nya teckensnitt gör att du kan anpassa den välbekanta konsol fönster upplevelsen.

### <a name="new-cmdlet-and-hosting-apis"></a>Ny cmdlet och värdbaserade API: er

Det nya API: et och värd-API: t inkluderar offentliga API: er för avancerad syntax (AST) och API: er för sid växling för pipeline, kapslade pipelines, körnings utrymme pooler, Windows RT, det föråldrade cmdlet-attributet och verb-och Substantiv egenskaperna för FunctionInfo-objektet.

### <a name="performance-improvements"></a>Prestandaförbättringar

Betydande prestanda förbättringar i Windows PowerShell kommer från den nya språk tolkare, som bygger på det dynamiska körnings språket (DLR) i .NET Framework 4. tillsammans med skript kompilering för körning, förbättringar av motorns tillförlitlighet och förändringar i algoritmen för `Get-ChildItem` att förbättra dess prestanda, särskilt vid sökning av nätverks resurser.

### <a name="runas-and-shared-host-support"></a>Stöd för RunAs och delad värd

Windows PowerShell 3,0 innehåller stöd för funktioner i RunAs och delade värdar.

Funktionen *runas* , som är utformad för Windows PowerShell-arbetsflöde, låter användare av en sessions konfiguration skapa sessioner som körs med behörigheten för ett delat användar konto. Detta gör det möjligt för mindre privilegierade användare att köra vissa kommandon och skript med administratörs behörighet och minskar behovet av att lägga till mindre erfarna användare i gruppen Administratörer.

Funktionen **SharedHost** gör att flera användare på flera datorer kan ansluta till en arbets flödes session samtidigt och övervaka förloppet för ett arbets flöde. Användare kan starta ett arbets flöde på en dator och sedan ansluta till arbets flödes sessionen på en annan dator utan att koppla från sessionen från den ursprungliga datorn. Användare måste ha samma behörigheter och ha samma konfiguration av sessionen. Mer information finns i "köra ett Windows PowerShell-arbetsflöde" i Komma igång med Windows PowerShell-arbetsflöde.

### <a name="special-character-handling-improvements"></a>Förbättringar av Special Character-hantering

För att förbättra möjligheten för Windows PowerShell 3,0 att tolka och korrekt hantera specialtecken, är parametern **LiteralPath** , som hanterar specialtecken i sökvägar, giltig i nästan alla cmdletar som har en **Sök vägs** parameter, inklusive nya `Update-Help` och `Save-Help` cmdletar. Parsern innehåller också särskild logik för att förbättra hanteringen av bakstrecks tecken ( \` ) och hakparenteser i fil namn och sökvägar.

## <a name="see-also"></a>Se även

- [about_Windows_PowerShell_5.0](/previous-versions/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
