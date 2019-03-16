---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Vad är nytt i Windows PowerShell 5.0
ms.openlocfilehash: a21e6af9f23ac8bb3ddf84dbfa67a67f3ff93b24
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055112"
---
# <a name="whats-new-in-windows-powershell-50"></a>Vad är nytt i Windows PowerShell 5.0

Windows PowerShell 5.0 innehåller nya viktiga funktioner som utökar användningen, förbättrar dess användbarhet och gör att du kan styra och hantera Windows-baserade miljöer enklare och mer omfattande.

Windows PowerShell 5.0 är bakåtkompatibla. Cmdlet: ar, leverantörer, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 4.0, Windows PowerShell 3.0 och Windows PowerShell 2.0 Allmänt fungerar i Windows PowerShell 5.0 utan ändringar.

## <a name="installing-windows-powershell"></a>Installera Windows PowerShell

Windows PowerShell 5.0 installeras som standard på Windows Server 2016 Technical Preview och Windows 10.

Om du vill installera Windows PowerShell 5.0 på Windows Server 2012 R2, Windows 8.1 Enterprise eller Windows 8.1 Pro, ladda ned och installera [Windows Management Framework 5.0](https://aka.ms/wmf5download). Glöm inte att läsa hämta information och uppfyller alla systemkrav, innan du installerar Windows Management Framework 5.0.

## <a name="in-this-topic"></a>I det här avsnittet

- [Uppdateringar av Windows PowerShell 4.0 DSC i KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nya funktioner i Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nya funktioner i Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nya funktioner i Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Samlad (KB 3000850) för Windows PowerShell 4.0 uppdateringar i November 2014-uppdatering

Många uppdateringar och förbättringar för Windows PowerShell Desired State Configuration (DSC) i Windows PowerShell 4.0 finns i den [November 2014-uppdatering för Windows RT 8.1, Windows 8.1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). Du kan fastställa om KB 3000850 är installerad på datorn genom att köra `Get-Hotfix -Id KB3000850` i Windows PowerShell.

- Uppdateringar av befintliga cmdletar i den [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modul
  - [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) är snabbare (särskilt i ISE).
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) har en ny parameter - UseExisting, som återställer senast tillämpade konfiguration.
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) -Force har åtgärdats.
  - [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) visar mer användbar information om motorn tillstånd.
  - [Test-DscConfiguration](https://technet.microsoft.com/library/dn407382.aspx) nu Returnerar namnet på datorn tillsammans med SANT eller FALSKT.
  - [Ny DscChecksum](https://technet.microsoft.com/library/dn521622.aspx) har nu stöd för UNC-sökvägar.

- Nya cmdletar i den [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modul
  - [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541(v=wps.630).aspx):  Utför en kontroll av pull begäran.
  - [Stop-DscConfiguration](https://technet.microsoft.com/library/mt143542(v=wps.630).aspx):  Stoppar en konfiguration som redan körs.
  - [Remove-DscConfigurationDocument](https://technet.microsoft.com/library/mt143544(v=wps.630).aspx):  Kan du ta bort konfigurationsdokument i olika faser (väntande, tidigare eller aktuella).

- Förbättringar av språk
  - DependsOn stöder nu sammansatta resurser.
  - DependsOn har nu stöd för tal i namn på resursen.
  - Noduttryck som utvärderas till tom inte längre genererar fel.
  - Ett fel som uppstår om en nod-uttrycket utvärderas till tom har åtgärdats.
  - Konfigurationer som anropar konfigurationer nu fungerar i Windows PowerShell-konsolen.

- Förbättringar av pull-läge
  - Pull-läge har nu stöd för alla ZIP-filer.
  - **AllowModuleOverwrite** fungerar nu korrekt.

- Förbättringar för återhämtning
  - Ny **DebugMode** kan du läsa in resursen moduler.
  - Om det inträffar ett fel i konfiguration, tas pending.mof-filen inte bort.
  - Den lokala Configuration Manager (LCM) är nu mer robust när metaconfiguration inställningar har skadats.

- Diagnostikförbättringar
  - En varning visas när LCM anger timern till andra inställningar än vad du har angett.
  - Fel loggfiler innehåller nu anropsstacken för Windows PowerShell-resurser.

- Förbättringar av flexibilitet
  - LocalConfigurationManager resursen har en ny egenskap **ActionAfterReboot**.
    - ContinueConfiguration (standardvärde): Återupptar automatiskt en konfiguration när en målnoden har startats om.
    - StopConfiguration: Fortsätt inte automatiskt en konfiguration när en nod startas om.
  - Kör en konsekvenskontroll kan nu oftare än en PULL-åtgärd eller vice versa.
  - Stöd för versionshantering:  DSC kan nu identifiera ett dokument som har genererats på en nyare klient (medföljer [WMF 5.0](https://aka.ms/wmf5download)).

- Fel dataförlustskydd förbättringar
  - Modulversion har nu verkställts innan en konfiguration tillämpas.
  - **DebugPreference** är nu korrekt för Get-, Set- eller Test-TargetResource anrop.

- Hantering av förbättringar av autentiseringsuppgifter
  - Ett certifikat används nu om både **certifikat** och **PSDscAllowPlainTextPassword** har angetts.
  - Autentiseringsuppgifterna dekrypteras, även för Get-TargetResource.
  - Metaconfiguration autentiseringsuppgifter krypteras och dekrypteras.
  - PSCredentials nu dekrypteras när de är i ett inbäddat objekt.

- Förbättringar av inbyggda resurs
  - Paket-resurs
    - Installerar inte längre fel paketet (antingen från lokala eller web källor).
    - Har nu stöd för HTTPS.
  - Det finns nu stöd för HTTPS i den [paketera resource](https://technet.microsoft.com/library/dn282132.aspx).
  - [Arkivera resursen](https://technet.microsoft.com/library/dn249917.aspx) stöder nu autentiseringsuppgifter.

## <a name="new-features-in-windows-powershell-50"></a>Nya funktioner i Windows PowerShell 5.0

- [Nya funktioner i Windows PowerShell](#new-features-in-windows-powershell)
- [Nya funktioner i Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nya funktioner i Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nya funktioner i Windows PowerShell-webbtjänster](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Viktiga felkorrigeringar i Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nya funktioner i Windows PowerShell

- Från och med Windows PowerShell 5.0, kan du utveckla med hjälp av klasser, med hjälp av formella syntax och semantik som påminner andra objektorienterat programmeringsspråk. **Klassen**, **Enum**, och andra nyckelord har lagts till i Windows PowerShell-språket för den nya funktionen. Mer information om hur du arbetar med klasser finns about_Classes.

- Windows PowerShell 5.0 introducerar en ny, strukturerade informationsström som du kan använda för att överföra strukturerade data mellan ett skript och dess anropare (eller värdmiljön). Du kan nu använda Write-värden för att generera utdata till en dataström med information. Informationsströmmar fungerar även för PowerShell.Streams, jobb, schemalagda jobb och arbetsflöden. Följande funktioner stöder information dataströmmen.
  - En ny cmdlet i Write-Information där du kan ange hanteringen av information strömdata för ett kommando i Windows PowerShell. Skriv-värden är en Omslutning för skrivning-Information. Skriv-informationen finns också en arbetsflödesaktivitet som stöds.
  - Två nya gemensamma parametrar, InformationVariable och InformationAction, kan du avgöra hur information dataströmmar från ett kommando visas. Giltiga värden för InformationAction är SilentlyContinue, stoppa, Fortsätt, Inquire, Ignorera eller pausa med SilentlyContinue standardvärdet. InformationVariable anger en sträng som namnet på en variabel som du vill skriva-Host-data från ett kommando som sparats.
  - En ny inställningsvariabeln InformationPreference, anger din standardprioritet för information strömdata i en Windows PowerShell-session. Standardvärdet är SilentlyContinue.
  - Två nya arbetsflödets gemensamma parametrar, PSInformation och InformationAction, har lagts till.
  - När du använder kommandot Format-Table formateras tabellkolumner nu automatiskt genom att utvärdera den första 300ms av data som skickas via dataströmmen.

- I samarbete med [Microsoft Research](https://research.microsoft.com/), en ny cmdlet, ConvertFrom-sträng, har lagts till. ConvertFrom-sträng kan du extrahera och parsa strukturerade objekt från innehållet i textsträngar. Mer information finns i ConvertFrom-sträng.
- En ny cmdlet för att konvertera-strängen formateras texten baserat på ett exempel som du anger i en - exempel-parameter.
- En ny modul Microsoft.PowerShell.Archive, innehåller cmdletar som kan du komprimera filer och mappar i (även kallat ZIP) arkivfiler, extrahera filerna från befintliga ZIP-filer och uppdatera ZIP-filer med nyare versioner av filer som komprimerats i dem.
- En ny modul PackageManagement, kan du identifiera och installera programvarupaket på Internet. Modulen PackageManagement (kallades tidigare OneGet) är en manager eller multiplexor av befintliga pakethanterare (kallas även för leverantörer av paketet) till en enhetlig pakethantering i Windows med ett enda Windows PowerShell-gränssnitt.
- En ny modul PowerShellGet, kan du hitta, installera, publicera och uppdatera moduler och DSC-resurser på den [PowerShell-galleriet](https://www.powershellgallery.com/), eller på en intern modul-lagringsplats som du kan ställa in genom att köra cmdleten Register-PSRepository.
- Ett nytt språk nyckelord, **Hidden**, har lagts till att ange att en medlem (en egenskap eller en metod) inte visas som standard i Get-Member resultat (om du lägger till parametern - Force). Egenskaper och metoder som har markerats som dolt också visas inte i IntelliSense resultat om du inte är i ett sammanhang där medlemmen ska vara synliga. till exempel automatisk variabeln $detta ska visa dolda medlemmar i klassmetoden.
- Nytt objekt, ta bort objekt och Get-ChildItem har förbättrats för att kunna skapa och hantera [symboliska länkar](https://en.wikipedia.org/wiki/Symbolic_link). Den **- ItemType** parametern för New-Item accepterar ett nytt värde **SymbolicLink**. Nu kan du skapa symboliska länkar i en enda rad genom att köra cmdlet New-objekt.
- Get-ChildItem har också en ny - djup parametern, som du använder med parametern - Recurse för att begränsa rekursion. Till exempel Get-ChildItem-Recurse - djup 2 returnerar resultat från den aktuella mappen, alla underordnade mappar inom den aktuella mappen och alla mappar inom underordnat mappar.
- Nu kan du kopiera filer och mappar från en Windows PowerShell-session till en annan, vilket innebär att du kan kopiera filer till sessioner som är anslutna till fjärrdatorer, Copy-Item (inklusive datorer som kör [Nano Server](https://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), och Därför har inga andra gränssnitt). Ange PSSession-ID: N som värde för de nya parametrarna - FromSession och -ToSession för att kopiera filer och Lägg till - sökväg och - mål för att ange sökväg till ursprung och mål, respektive. Till exempel kopiera objekt-sökväg c:\\myFile.txt - ToSession $s-mål d:\\destinationFolder.
- Windows PowerShell-avskrift har förbättrats för att tillämpa för alla värdbaserade program (till exempel Windows PowerShell ISE) förutom konsolvärden (**powershell.exe**). Transkription alternativ (inklusive aktiverar systemomfattande avskrifter) kan konfigureras genom att aktivera den **aktivera PowerShell avskrift** gruppolicy-inställningen finns i administrativa mallar/Windows komponenter/Windows PowerShell.
- En ny funktion för spårning av detaljerade skript kan du aktivera detaljerad spårning och analys av Windows PowerShell skript används på ett system. När du har aktiverat detaljerad skriptet spårning av Windows PowerShell loggar alla skriptblocken händelseloggen Event Tracing för Windows (ETW) **Microsoft-Windows-PowerShell/Operational**.
- Från och med Windows PowerShell 5.0, den nya syntaxen Cryptographic Message Syntax cmdletar stöder kryptering och dekryptering av innehåll med hjälp av IETF standardformat för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](https://tools.ietf.org/html/rfc5652). Cmdlet: Get-CmsMessage, skydda CmsMessage och Unprotect CmsMessage har lagts till i [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh849807.aspx) modulen.
- Nya cmdletar i den [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modulen, Get-Körningsutrymme, Debug Runspace, Get-RunspaceDebug, aktivera RunspaceDebug och inaktivera RunspaceDebug låter dig ange felsökningsalternativ på en körningsutrymme och starta och stoppa Felsökning på ett körningsutrymme. För felsökning av godtycklig körningsutrymmen (det vill säga körningsutrymmen som inte är standard körningsutrymme för en Windows PowerShell-konsolen eller Windows PowerShell ISE-session) kan Windows PowerShell du ange brytpunkter i ett skript och har lagt brytpunkter Stoppa skriptet från körs tills du kan koppla en felsökare för att felsöka skriptet körningsutrymme. Stöd för kapslade felsökning för godtycklig körningsutrymmen har lagts till felsökningsprogram för Windows PowerShell-skript för körningsutrymmen.
- En ny Format-Hex-cmdlet har lagts till i [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modulen. Hexadecimalt format kan du visa text eller binära data i hexadecimalt format.
- Get-Urklipp och Set-Urklipp cmdletar har lagts till i [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modulen; de underlättar överföringen av innehåll till och från en Windows PowerShell-session. Urklipps-cmdletar har stöd för bilder, ljudfiler, fillistor och text.
- En ny cmdlet, Clear-RecycleBin har lagts till i [Microsoft.PowerShell.Management](https://technet.microsoft.com/library/hh849827(v=wps.640).aspx) modul; den här cmdleten förbrukade återvinningen Bin för en fast enhet som innehåller externa enheter. Som standard uppmanas du att bekräfta en Clear-RecycleBin-kommandot, eftersom egenskapen ConfirmImpact i cmdleten är inställd på ConfirmImpact.High.
- En ny cmdlet New-TemporaryFile, kan du skapa en temporär fil som en del av skript. Som standard skapas den nya tillfälliga filen i ```C:\Users\<user name>\AppData\Local\Temp```.
- Out-File, Lägg till innehållet och Set-Content-cmdletar nu har en ny - NoNewline-parametern, som utesluter en ny rad efter utdatan.
- Cmdlet New-Guid: en använder .NET Framework Guid-klassen för att generera ett GUID, som är användbara när du skriver skript eller DSC-resurser.
- Eftersom filversionsinformation kan vara vilseledande, särskilt när en fil är uppdaterad, finns nya FileVersionRaw och ProductVersionRaw skriptegenskaper FileInfo-objekt. Du kan till exempel köra följande kommando för att visa värdena i de här egenskaperna för powershell.exe, där $pid innehåller process-ID för en aktiv Windows PowerShell-session:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```
- Nya cmdletar RETUR PSHostProcess och avsluta PSHostProcess kan du felsöka Windows PowerShell-skript i processer som är separat från den aktuella processen som körs i Windows PowerShell-konsolen. Kör RETUR-PSHostProcess för att ange eller ansluta till en särskild process-ID och sedan köra Get-Körningsutrymme för att returnera active körningsutrymmen i processen. Kör avsluta PSHostProcess kopplar du bort från processen när du är klar med att felsöka ett skript i processen.
- En ny cmdlet för Wait-felsökare har lagts till i [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modulen. Du kan köra Wait-felsökare för att stoppa ett skript i felsökningsprogrammet innan du kör instruktionen nästa i skriptet.
- Windows PowerShell Workflow-felsökare har nu stöd för kommando eller fliken slutförande och du kan felsöka kapslat arbetsflödesfunktioner. Du kan nu trycka på **Ctrl + Break** ska kunna starta felsökningsprogram i ett skript som körs i både lokala och fjärranslutna sessioner och i ett för arbetsflödesskript.
- En Debug-Job-cmdlet har lagts till i [Microsoft.PowerShell.Core](https://technet.microsoft.com/library/hh849695.aspx) modul för att felsöka skript som körs jobbet för Windows PowerShell-arbetsflöde, bakgrund och jobb som körs i fjärrsessioner.
- En ny status, AtBreakpoint, har lagts till för Windows PowerShell-jobb. Skriptet har nått en brytpunkt AtBreakpoint tillståndet gäller när ett jobb körs ett skript som innehåller ange brytpunkter. När ett jobb har stoppats på en debug brytpunkt, måste du felsöka jobbet genom att köra cmdleten Debug-jobbet.
- Windows PowerShell 5.0 implementerar stöd för flera versioner av en enda Windows PowerShell-modul i samma mapp i $PSModulePath. En RequiredVersion-egenskap har lagts till klassen ModuleSpecification för att du får den önskade versionen av modulen. den här egenskapen är ömsesidigt uteslutande med egenskapen ModuleVersion. RequiredVersion stöds nu som en del av värdet för parametern FullyQualifiedName för Get-Module Import-Module och Remove-Module-cmdletar.
- Du kan nu utföra modulen version verifieringen genom att köra cmdleten Test-ModuleManifest.
- Resultatet för Get-Command-cmdlet visar nu en versionskolumn; en ny Version-egenskap har lagts till CommandInfo-klassen. Get-Command visar kommandon från flera versioner av samma modul. Egenskapen Version ingår också i härledda klasser av CmdletInfo: CmdletInfo och ApplicationInfo.
- Get-Command har en ny parameter - ShowCommandInfo, som returnerar ShowCommand information som PSObjects. Detta är särskilt användbar funktion för när Show-kommandot har körts i Windows PowerShell ISE med hjälp av Windows PowerShell-fjärrkommunikation. Ersätter befintlig Get-SerializedCommand-funktion i modulen Microsoft.PowerShell.Utility för parametern - ShowCommandInfo Get-SerializedCommand skriptet är dock fortfarande för att stödja äldre skript.
- En ny cmdlet Get-ItemPropertyValue kan du hämta värdet för en egenskap utan med hjälp av punktnotation. Du kan till exempel köra följande kommando för att hämta värdet för egenskapen Programbas för registernyckeln PowerShellEngine i äldre versioner av Windows PowerShell: **(Get-itemproperty-egenskap-sökvägen HKLM:\\programvara\\Microsoft\\PowerShell\\3\\PowerShellEngine-namnge ApplicationBase). ApplicationBase**. Från och med Windows PowerShell 5.0, kan du köra **Get-ItemPropertyValue-sökvägen HKLM:\\programvara\\Microsoft\\PowerShell\\3\\PowerShellEngine-namnet ApplicationBase** .
- Windows PowerShell-konsolen använder nu syntaxfärgning, precis som för Windows PowerShell ISE.
- En ny NetworkSwitch-modulen innehåller cmdlets som hjälper dig att använda växeln, virtuellt LAN (VLAN) och grundläggande nivå 2-portkonfiguration av nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar.
- Parametern FullyQualifiedName har lagts till Import-Module och Remove-Module-cmdletar för lagring av flera versioner av en enda modul.
- Save-Help, Update-Help, Import-PSSession, Export-PSSession och Get-Command har du en ny parameter FullyQualifiedModule av typen ModuleSpecification. Lägg till den här parametern om du vill ange en modul med dess fullständigt kvalificerade namn.
- Värdet för **$PSVersionTable.PSVersion** har uppdaterats till 5.0.
- WMF 5.0 (PowerShell 5.0) innehåller den **Pester** modulen.  Lära är en enhet som xcuitest för PowerShell. Det ger ett par enkla att använda nyckelord som kan du skapa tester för dina skript.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nya funktioner i Windows PowerShell Desired State Configuration

- Förbättringar av Windows PowerShell-språket kan du definiera resurser för Windows PowerShell Desired State Configuration (DSC) med hjälp av klasser. Import-DscResource är nu en SANT dynamisk nyckelord. Windows PowerShell tolkar rotmodul för den angivna modulen, söker efter klasser som innehåller attributet DscResource. Du kan nu använda klasser för att definiera DSC-resurser, där varken en MOF-fil eller en DSCResource undermapp i modulmappen krävs. En fil för Windows PowerShell-modulen kan innehålla flera DSC-resursklasser.
- En ny parameter ThrottleLimit, har lagts till i följande cmdletar i modulen PSDesiredStateConfiguration. Lägg till parametern ThrottleLimit för att ange hur många datorer eller enheter som du vill att kommandot ska fungera på samma gång.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Med centraliserade DSC felrapportering loggas omfattande felinformation inte bara i event log, men den kan skickas till en central plats för senare analys. Du kan använda den här centrala platsen för att lagra DSC-konfigurationsfel som har inträffat för server i sin miljö. När rapportservern har definierats i metadata-konfiguration, alla fel skickas till rapportservern, och sedan lagras i en databas. Du kan ställa in den här funktionen, oavsett om huruvida en målnoden har konfigurerats för att hämta konfigurationer från en pull-server.
- Förbättringar av Windows PowerShell ISE underlättar redigering av DSC-resurs. Du kan nu göra följande.
  - Lista över alla DSC-resurser i en **configuration** eller **nod** block genom att ange **Ctrl + blanksteg** på en tom rad i blocket.
  - Automatisk komplettering på resursegenskaperna för den **uppräkning** typen.
  - Automatisk komplettering på den **DependsOn** egenskapen för DSC-resurser, baserat på andra resursinstanser i konfigurationen.
  - Förbättrad tabbifyllning för egenskapsvärden för resurs.
- En användare kan nu köra en resurs under en angiven uppsättning autentiseringsuppgifter genom att lägga till den **PSDscRunAsCredential** attribut i en nod-blocket. Till exempel PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Den här funktionen är användbar för att skapa konfigurationer som kör Windows Installer och körbart installationsprogram, få åtkomst till registreringsdatafilen per användare eller utföra andra åtgärder utanför aktuellt användarsammanhang.
- stöd för 32-bitars (x86-baserad) har lagts till för den **Configuration** nyckelord.
- Windows PowerShell har nu stöd för anpassade hjälp för DSC-konfigurationer, som fastställs genom att lägga till \[CmdletBinding()] till funktionen skapade konfigurationen.
- En ny **DscLocalConfigurationManager** attributet betecknar ett block med konfigurationen som en meta-konfiguration, som används för att konfigurera DSC Local Configuration Manager. Det här attributet begränsar en konfiguration som ska som innehåller endast de objekt som konfigurerar DSC Local Configuration Manager. Under bearbetning, den här konfigurationen genererar en \*. meta.mof-fil som sedan skickas till lämplig målnoder genom att köra cmdlet Set-DscLocalConfigurationManager.
- Partiella konfigurationer tillåts nu i Windows PowerShell 5.0. Du kan leverera configuration dokument till en nod i fragment. För en nod tar emot flera fragment av en konfigurationsdokumentet måste nodens Local Configuration Manager anges först ange förväntade fragment
- Cross-datorsynkronisering är ny i DSC i Windows PowerShell 5.0. Med hjälp av inbyggda WaitFor\* resurser (**WaitForAll**, **WaitForAny**, och **WaitForSome**), kan du nu ange beroenden mellan datorer under konfigurationen körs utan externa orkestreringar. Dessa resurser innehåller synkronisering av nod-till-nod med hjälp av CIM-anslutningar via protokollet WS-Man. En konfiguration kan vänta på en annan dator resurstillståndet att ändra.
- Bara tillräckligt Administration (JEA), en ny delegering säkerhetsfunktion, använder DSC och Windows PowerShell begränsade körningsutrymmen att hjälpa företag att säkra från dataförlust eller kompromettering av anställda, om avsiktlig och oavsiktlig. Läs mer om JEA, inklusive där du kan hämta xJEA DSC-resurs [Just Enough Administration, steg för steg](https://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).
- Följande nya cmdletar har lagts till modulen PSDesiredStateConfiguration.
  - En ny cmdlet Get-DscConfigurationStatus hämtar översiktlig information om Konfigurationsstatus från en målnoden. Du kan hämta status för senast eller för alla konfigurationer.
  - En ny jämför-DscConfiguration-cmdleten jämför en angiven konfiguration med en eller flera målnoder bibliotekets tillstånd.
  - En ny publicera-DscConfiguration-cmdleten kopierar en MOF-konfigurationsfilen till en målnod, men de gäller inte konfigurationen. Konfigurationen används under nästa konsekvens passet eller när du kör Update-DscConfiguration-cmdleten.
  - En ny Test-DscConfiguration-cmdleten kan du verifiera att en resulterande konfigurationen matchar den önskade konfigurationen, returnera värdet SANT om konfigurationen matchar önskad konfiguration eller falskt om den faktiska konfigurationen inte matchar den önskade konfiguration.
  - En ny uppdatering-DscConfiguration-cmdleten tvingar en konfiguration som ska bearbetas. Om den lokala Konfigurationshanteraren finns i pull-läge, hämtar cmdlet: en konfigurationen från hämtningsservern innan den tillämpas.

### <a name="new-features-in-windows-powershell-ise"></a>Nya funktioner i Windows PowerShell ISE

- Du kan nu redigera fjärransluten Windows PowerShell-skript och filer i en lokal kopia av Windows PowerShell ISE genom att köra Enter-PSSession för att starta en fjärrsession på den dator som lagrar de filer du vill redigera och kör sedan **PSEdit \<sökvägen och filnamnet på fjärrdatorn\>**. Den här funktionen förenklar redigering Windows PowerShell-filer som lagras på en Server Core-installation av Windows Server, där Windows PowerShell ISE inte kan köras.
- Cmdleten Start-avskrift stöds nu i Windows PowerShell ISE.
- Du kan nu felsöka remote skript i Windows PowerShell ISE.
- Ett nytt kommando **bryta alla** (Ctrl + F) delar in i felsökaren för både lokala och via en fjärranslutning med skript.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nya funktioner i Windows PowerShell-webbtjänster (Management OData IIS Extension)

- Från och med Windows PowerShell 5.0, kan du generera en uppsättning Windows PowerShell-cmdletar baserade på de funktioner som exponeras av en viss OData-slutpunkten genom att köra cmdleten Export-ODataEndpointProxy hittades i den nya [ Microsoft.PowerShell.OdataUtils](https://technet.microsoft.com/library/dn818507(v=wps.640).aspx) modulen.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Viktiga felkorrigeringar i Windows PowerShell 5.0

- Windows PowerShell 5.0 innehåller en ny COM-implementering, vilket ger betydande prestandaförbättringar när du arbetar med COM-objekt. Läs en videodemonstration av effekten [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Betydande förbättringar har gjorts till den första tabbifyllning i en Windows PowerShell-session förkortar fliken tid för slutförande av nästan 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nya funktioner i Windows PowerShell 4.0

Windows PowerShell 4.0 är bakåtkompatibla. Cmdlet: ar, leverantörer, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 3.0 och Windows PowerShell 2.0 fungerar i Windows PowerShell 4.0 utan ändringar.

Windows PowerShell 4.0 är installerat som standard på Windows 8.1 och Windows Server 2012 R2. Om du vill installera Windows PowerShell 4.0 på Windows 7 med SP1 eller Windows Server 2008 R2, ladda ned och installera [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855). Glöm inte att läsa hämta information och uppfyller alla systemkrav, innan du installerar Windows Management Framework 4.0.

- [Nya funktioner i Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nya funktioner i Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nya funktioner i Windows PowerShell-arbetsflöde](#new-features-in-windows-powershell-workflow)
- [Nya funktioner i Windows PowerShell-webbtjänster](#new-features-in-windows-powershell-web-services)
- [Nya funktioner i Windows PowerShell-webbåtkomst](#new-features-in-windows-powershell-web-access)
- [Viktiga felkorrigeringar i Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 innehåller följande nya funktioner.

### <a name="new-features-in-windows-powershell"></a>Nya funktioner i Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) är en ny system i Windows PowerShell 4.0, som gör det möjligt för distribution och hantering av konfigurationsdata för Programvarutjänster och miljön där de här tjänsterna körs. Läs mer om DSC [Kom igång med Windows PowerShell Desired State Configuration](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).
- **Save-Help** nu kan du spara hjälp för moduler som är installerade på fjärrdatorer. Du kan använda Save-Help för att hämta modulen hjälp från en Internetansluten klient (där inte alla moduler som du vill ha hjälp nödvändigtvis installeras) och sedan kopiera sparade hjälp till en delad fjärrmapp eller en fjärrdator som inte är ansluten till Internet åtkomst.
- Windows PowerShell-felsökare har förbättrats för att tillåta felsökning av Windows PowerShell-arbetsflöden, samt skript som körs på fjärrdatorer. Windows PowerShell-arbetsflöden kan nu felsökas på skriptnivån från Windows PowerShell-kommandoraden eller i Windows PowerShell ISE. Windows PowerShell-skript, inklusive skriptarbetsflöden, kan nu att den felsöks över fjärrsessioner. Felsökning fjärrsessioner bevaras över fjärransluten Windows PowerShell-sessioner som är frånkopplad och därefter ansluts igen senare.
- En **RunNow** parametern för **Register-ScheduledJob** och **Set-ScheduledJob** eliminerar behovet av att ange en omedelbar startdatum och starttid för jobb med hjälp av **Utlösaren** parametern.
- **Invoke-RestMethod** och **Invoke-WebRequest** nu kan du ange alla rubriker med hjälp av parametern rubriker. Även om den här parametern har alltid fanns var det en av flera parametrar för web-cmdletar som resulterade i fel eller undantag.
- **Get-Module** har en ny parameter **FullyQualifiedName**, av typen **ModuleSpecification\[]**. Den **FullyQualifiedName** -parametern för Get-Module nu kan du ange en modul med hjälp av modulens namn, version och du kan också dess GUID.
- Standardprincipinställningen för körning på Windows Server 2012 R2 är **RemoteSigned**. Det finns ingen ändring i inställningen på Windows 8.1.
- Från och med Windows PowerShell 4.0, stöds metodanropet med hjälp av dynamisk metodnamn. Du kan använda en variabel för att lagra ett metodnamn och sedan anropa metoden dynamiskt genom att anropa variabeln.
- Asynkron arbetsflödesjobb är inte längre bort när tidsgränsen som anges av den **PSElapsedTimeoutSec** gemensamma arbetsflödesparametern har gått ut.
- En ny parameter **RepeatIndefinitely**, har lagts till i **New-JobTrigger** och **Set-JobTrigger** cmdletar. Detta eliminerar behovet av att ange en **TimeSpan.MaxValue** värde för den **RepetitionDuration** parameter för att köra ett schemalagt jobb flera gånger på obestämd tid.
- En **Passthru** parameter har lagts till i **Enable-JobTrigger** och **Disable-JobTrigger** cmdletar. Passthru-parametern visas alla objekt som skapas eller ändras av kommandot.
- Parameternamn för att ange en arbetsgrupp i den **Lägg till dator** och **Remove-Computer** cmdletar nu är konsekventa. Båda cmdletarna nu använder du parametern **arbetsgruppsnamnet**.
- En ny vanliga parameter **PipelineVariable**, har lagts till. PipelineVariable kan du spara resultatet av en via rörledningar kommandot (eller en del av ett via rörledningar kommando) som en variabel som kan skickas via resten av pipelinen.
- Samling filtrering med hjälp av en metodsyntax stöds nu. Det innebär att du kan nu filtrera en uppsättning objekt med hjälp av förenklad syntax, liknande den för WHERE () eller Where-Object, formaterad som ett metodanrop. Följande är ett exempel: (Get-Process) .where ({$_. Name - matchar ”powershell”})
- Den **Get-Process** cmdlet har en ny switchparameter **IncludeUserName**.
- En ny cmdlet **Get-FileHash**, som returnerar ett hash-värdet i flera olika format för en angiven fil, har lagts till.
- I Windows PowerShell 4.0, om en modul använder den **DefaultCommandPrefix** nyckeln i manifestet, eller om du importerar en modul med det **prefixet** parameter, den **ExportedCommands**egenskapen för modulen visar kommandon i modulen med prefixet. När du kör kommandona med hjälp av modulkvalificerade syntax ModuleName\\CommandName, kommandonamn måste innehålla prefixet.
- Värdet för **$PSVersionTable.PSVersion** har uppdaterats till 4.0.
- **WHERE ()** operatorn uppträdandet har förändrats. `Collection.Where('property -match name')` tar emot ett stränguttryck i formatet `"Property -CompareOperator Value"` stöds inte längre. Men den **WHERE ()** operatör accepterar stränguttryck i formatet av en scriptblock; detta fortfarande stöds.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nya funktioner i Windows PowerShell Integrated Scripting Environment (ISE)

- Windows PowerShell ISE stöder både Windows PowerShell-arbetsflöde felsökning och felsökning av fjärråtkomst skript.
- IntelliSense-stöd har lagts till för Windows PowerShell Desired State Configuration-leverantörer och konfigurationer.

### <a name="new-features-in-windows-powershell-workflow"></a>Nya funktioner i Windows PowerShell-arbetsflöde

- Stöd har lagts till för en ny **PipelineVariable** gemensamma parametern i samband med iterativ pipelines, till exempel de som används av System Center Orchestrator, det vill säga pipelines som kör kommandon bara vänster till höger, inte bland kör med hjälp av strömning.
- Parameterbindningen har förbättrats avsevärt för att fungera utanför fliken slutförande scenarier, till exempel med kommandon som inte finns i det aktuella körningsutrymmet.
- Stöd för anpassad behållare aktiviteter har lagts till Windows PowerShell-arbetsflöde. Om en aktivitetsparameter är av typerna **aktivitet**, **aktivitet\[]** (eller är en allmän uppsättning aktiviteter) och användaren har skickat ett skriptblock med som ett argument, sedan Windows PowerShell Arbetsflödet konverterar skriptblocket till XAML, precis som med normal Windows PowerShell-skript-arbetsflöde kompilering.
- Efter en krasch återansluter Windows PowerShell-arbetsflöde automatiskt till hanterade noder.
- Du kan nu begränsa **Foreach-Parallel** aktivitet uttryck med hjälp av den **ThrottleLimit** egenskapen.
- Den **ErrorAction** gemensamma parametern har ett nytt giltigt värde **Suspend**, det vill säga exklusivt för arbetsflöden.
- En slutpunkt för arbetsflödet nu stängs automatiskt om det finns inga aktiva sessioner, inga pågående jobb och inga väntande jobb. Den här funktionen sparar resurser på den dator som fungerar som arbetsflödesservern, när automatisk avslutas villkor är uppfyllda.

### <a name="new-features-in-windows-powershell-web-services"></a>Nya funktioner i Windows PowerShell-webbtjänster

- När ett fel uppstår i Windows PowerShell-webbtjänster (PSWS, även kallad Management OData IIS Extension), samtidigt som körs en cmdlet mer detaljerade fel som returneras till anroparen. Dessutom felkoder följer [Windows Azure REST API felkod riktlinjer](https://msdn.microsoft.com/library/windowsazure/dd179357.aspx).
- En slutpunkt kan nu definiera API-versionen, samt framtvinga användningen av en viss API-version. När det inträffar version matchningsfel mellan klienten och servern, visas fel för både klienten och servern.
- Hantering av dispatch-schemat har förenklats genom att automatiskt generera värden för alla fält som saknas i schemat. Generation uppstår som en användbar utgångspunkt, även om dispatch-schemat inte finns.
- Typ av hantering i PSWS har förbättrats för att stödja typer som använder en annan konstruktor än Standardkonstruktorn av fungerar på samma sätt till den **standardkonstruktor** i Windows PowerShell. På så sätt kan du använda komplexa typer av PSWS.
- PSWS kan nu utökar en associerad instans när du kör en fråga. Överföring kostnaden är betydande för större binärt innehåll (till exempel bilder, ljud eller video), och är det bättre att överföra binära data utan kodning. PSWS använder namngivna resource strömmar för att överföra utan kodning. Den namngivna resursström är en egenskap för en entitet av den **Edm.Stream** typen. Varje namngiven resursström har en separat URI för GET eller UPDATE-åtgärder.
- OData-åtgärder ger nu en mekanism för att anropa metoder för icke-CRUD (skapa, läsa, uppdatera och ta bort) på en resurs. Du kan anropa en åtgärd genom att skicka en HTTP POST-begäran till URI: N som har definierats för åtgärden. Parametrar för åtgärden har definierats i brödtexten i POST-begäran.
- Om du vill att det stämmer överens med Windows Azure-riktlinjer, bör alla URL: er förenklas. En ändring som ingår i **nyckel som Segment** tillåter enkel nycklar representeras segment. Observera att referenser som använder flera nyckelvärden kräver fil med kommaavgränsade värden i parentetiska format, som tidigare.
- Innan den här versionen av PSWS, det endast operations var att anropa efter sätt för att utföra skapa, uppdatera eller ta bort, TOP- eller ta bort en resurs på toppnivå. Nytt i den här versionen av PSWS användarna innehöll resursåtgärder kan uppnå samma resultat när du når samma resurs mindre direkt närmar sig som om resurserna fanns.

### <a name="new-features-in-windows-powershell-web-access"></a>Nya funktioner i Windows PowerShell-webbåtkomst

- Du kan koppla från och återansluta till befintliga sessioner i den webbaserade Windows PowerShell Web Access-konsolen. En **spara** knappen i den webbaserade konsolen kan du koppla från en session utan att ta bort den och återansluta till sessionen som en annan tid.
- Standardparametrar kan visas på sidan logga in. Om du vill visa standardparametrar konfigurera värden för alla inställningar som visas i den **valfria anslutningsinställningar** tänkbara inloggningssidan i en fil med namnet **web.config**. Du kan använda den **web.config** filen för att konfigurera alla valfria anslutningsinställningar utom en andra eller en annan uppsättning autentiseringsuppgifter.
- I Windows Server 2012 R2, kan du fjärrhantera auktoriseringsregler för Windows PowerShell Web Access. Den **Add-PswaAuthorizationRule** och **Test-PswaAuthorizationRule** cmdletar omfattar nu en parameter för autentiseringsuppgifter som gör att administratörer kan hantera auktoriseringsregler från en fjärrdator eller i en Windows PowerShell Web Access-session.
- Du kan nu ha flera Windows PowerShell Web Access-sessioner i en enda webbläsarsession genom att använda en ny webbläsarflik för varje session. Du behöver inte längre att öppna en ny webbläsarsession för att ansluta till en ny session i den webbaserade Windows PowerShell-konsolen.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Viktiga felkorrigeringar i Windows PowerShell 4.0

- **Get-Counter** nu återgå räknare som innehåller en apostroftecknet i franska versioner av Windows.
- Nu kan du visa den **GetType** -metoden i avserialiserat objekt.
- **#Requires** uttryck ger nu användarna som kräver administratörsbehörighet, om det behövs.
- Den **importera Csv** cmdlet nu ignorerar tomma rader.
- Ett problem där Windows PowerShell ISE använder för mycket minne när du kör en **Invoke-WebRequest** kommando har åtgärdats.
- **Get-Module** visas nu modulversioner i en **Version** kolumn.
- Remove-Item - Recurse nu tar bort objekt från undermappar som förväntat.
- En **användarnamn** egenskapen har lagts till **Get-Process** mata ut objekt.
- Den **Invoke-RestMethod** cmdlet returnerar nu alla tillgängliga resultat.
- **Lägg till medlem** nu börjar gälla på hash-tabeller, även om de hash-tabeller som ännu inte har öppnats.
- **Select-Object - Expandera** inte längre misslyckas eller genererar ett undantag om värdet för egenskapen är null eller tomt.
- **Get-Process** kan nu användas i en pipeline med andra kommandon som får den **ComputerName** egenskap från objekt.
- **ConvertTo-Json** och **ConvertFrom-Json** går nu att använda termer inom dubbla citattecken och dess felmeddelanden är nu lokaliserbara.
- **Get-Job** nu returnerar någon slutförts schemalagda jobb, även i nya sessioner.
- Problem med att montera och demontera VHD: er med hjälp av den **filsystem** provider i Windows PowerShell 4.0 har åtgärdats. Windows PowerShell är nu kunna identifiera nya enheter när de är monterade i samma session.
- Du inte längre behöver du uttryckligen läsa in **ScheduledJob** eller **arbetsflöde** moduler att arbeta med sina jobbtyper.
- Prestandaförbättringar har gjorts att importera arbetsflöden som definierar kapslade arbetsflöden. den här processen är nu snabbare.

## <a name="new-features-in-windows-powershell-30"></a>Nya funktioner i Windows PowerShell 3.0

Windows PowerShell 3.0 innehåller följande nya funktioner.

- [Windows PowerShell-arbetsflöde](#windows-powershell-workflow)
- [Windows PowerShell-webbåtkomst](#windows-powershell-web-access)
- [Nya funktioner för Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Stöd för Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Stöd för Windows Preinstallation Environment](#support-for-windows-preinstallation-environment)
- [Frånkopplade sessioner](#disconnected-sessions)
- [Robust Session anslutning](#robust-session-connectivity)
- [Uppdateringsbar hjälpsystem](#updatable-help-system)
- [Förbättrad onlinehjälp](#enhanced-online-help)
- [CIM-integrering](#cim-integration)
- [Konfigurationsfiler för session](#session-configuration-files)
- [Schemalagda jobb och uppgiften Scheduler-integrering](#scheduled-jobs-and-task-scheduler-integration)
- [Förbättringar i Windows PowerShell-språket](#windows-powershell-language-enhancements)
- [Ny Kärncmdletar](#new-core-cmdlets)
- [Förbättringar av befintliga Core-Cmdlets och Providers](#improvements-to-existing-core-cmdlets-and-providers)
- [Remote modulimport och identifiering](#remote-module-import-and-discovery)
- [Förbättrad Tabbifyllning](#enhanced-tab-completion)
- [Modulen automatisk inläsning](#module-auto-loading)
- [Modulen Upplevelseförbättringar](#module-experience-improvements)
- [Förenklad kommandot identifiering](#simplified-command-discovery)
- [Förbättrad loggning, diagnostik och stöd för grupper i principen](#improved-logging-diagnostics-and-group-policy-support)
- [Formatering och förbättringar av utdata](#formatting-and-output-improvements)
- [Förbättrad värd-Webbkonsol](#enhanced-console-host-experience)
- [Ny Cmdlet och som är värd för API: er](#new-cmdlet-and-hosting-apis)
- [Prestandaförbättringar](#performance-improvements)
- [Kör och stöd för delade värd](#runas-and-shared-host-support)
- [Förbättringar för hantering av specialtecken](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell-arbetsflöde

Windows PowerShell-arbetsflöde får du kraften hos Windows Workflow Foundation på Windows PowerShell. Du kan skriva arbetsflöden i XAML eller i Windows PowerShell-språket och kör dem precis som du vill köra en cmdlet. Den [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet hämtar arbetsflödeskommandon och [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) hämtar hjälp för arbetsflöden.

Arbetsflöden är sekvenser av multicomputer hanteringsaktiviteter som är långvariga, upprepbara, frekventa, stöder parallellkörning, kan kopplas ifrån, suspendable och kan startas om. Arbetsflöden kan återupptas från ett avsiktliga och oavsiktliga avbrott, till exempel ett nätverksavbrott, en omstart av Windows eller ett strömavbrott.

Arbetsflöden är också portabla; de kan exporteras som eller importeras från XAML-filer. Du kan skriva anpassade sessionskonfigurationer som tillåter arbetsflöde eller aktiviteter i ett arbetsflöde som ska köras av delegerade eller underordnade användare.

Följande är fördelarna med Windows PowerShell-arbetsflöde

- Automatisering av sekvenserade, långvariga uppgifter.
- **Fjärrövervakning av långvariga aktiviteter**. Status och förlopp för aktiviteter är synliga när som helst.
- **Multicomputer hantering.** Samtidigt köra uppgifter som arbetsflöden på hundratals hanterade noder. Windows PowerShell-arbetsflöde innehåller ett inbyggt bibliotek med vanliga parametrar, t.ex **PSComputerName**, vilket möjliggör scenarier för hantering av flera datorer.
- **Aktivitet för körning av komplexa processer.** Du kan kombinera relaterade skript som implementerar ett helt scenario för slutpunkt till slutpunkt i ett enda arbetsflöde.
- **Persistence.** : ett arbetsflöde sparas (eller kontrollera visade) vid specifika tidpunkter som definierats av författaren så att du kan återuppta arbetsflödet från senast sparade aktivitet (eller kontrollpunkt), i stället för att starta om arbetsflödet från början.
- **Stabilitet.** Återställning av automatisk fel. Arbetsflöden klarar planerade och oplanerade omstarter. Du kan pausa arbetsflödeskörning och återuppta arbetsflödet från den sista punkten för persistence. Arbetsflödesskapare kan ange specifika aktiviteter att köra om fel uppstår på en eller flera hanterade noder.
- **Möjligheten att koppla ifrån, återansluta och körs i sessionen.** Användare kan ansluta och koppla från arbetsflödesservern, men arbetsflödet körs kontinuerligt. Du kan logga ut från klientdatorn eller starta om klientdatorn och övervaka arbetsflödeskörning från en annan dator utan att avbryta arbetsflödet.
- **Scheduling.** Uppgifter i arbetsflödet kan schemaläggas som alla Windows PowerShell-cmdlet eller ett skript.
- **Arbetsflödet och begränsning av anslutningen.** Arbetsflödeskörning och anslutningar till noderna kan vara begränsad, vilket gör att scenarier för skalbarhet och hög tillgänglighet.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access

Windows PowerShell-webbåtkomst är en funktion i Windows Server 2012 som användarna kan köra Windows PowerShell-kommandon och skript i en webbaserad konsol. Enheter som använder den webbaserade konsolen kräver inte Windows PowerShell, fjärrhanteringsprogramvara eller plugin-programmet installationer i webbläsaren. Allt som krävs är en korrekt konfigurerad Windows PowerShell Web Access-gateway och en webbläsare som stöder JavaScript och accepterar cookies.

Mer information finns i [distribuera Windows PowerShell-webbåtkomst](https://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nya funktioner för Windows PowerShell ISE

För Windows PowerShell 3.0, Windows PowerShell Integrated Scripting Environment (ISE) har många nya funktioner, inklusive IntelliSense, Show-kommandofönstret enhetlig konsolfönstret kodfragment, klammerparentes matchning, Visa-Dölj avsnitt, spara automatiskt, de senaste objekten lista, omfattande kopia, blockera kopiera och fullständigt stöd för att skriva arbetsflöden för Windows PowerShell-skript. Mer information finns i [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Stöd för Microsoft .NET Framework 4

Windows PowerShell skapas mot Common Language Runtime 4.0. Cmdlet: en, skript och arbetsflödesskapare kan använda de nya Microsoft .NET Framework 4-klasserna i Windows PowerShell med funktioner som innehåller programkompatibilitet och distribution, hanteras utökningsbarhet Framework, parallell datorbearbetning, nätverk, Windows Communication Foundation och Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Stöd för Windows Preinstallation Environment

Windows PowerShell 3.0 är en valfri komponent i Windows Preinstallation Environment (Windows PE) 4.0 för Windows 8. Windows PE är ett minimalt operativsystem som startar en dator där inget operativsystem och förbereder den för installation av Windows. Windows PE kan användas för att partitionera och formatera hårddiskar, kopiera diskavbildningar till en dator och starta installationsprogrammet för Windows från en nätverksresurs. Windows PowerShell 3.0 kan användas på Windows PE för att hantera distributionen, diagnostik och återställningsscenarier.

### <a name="disconnected-sessions"></a>Frånkopplade sessioner

Från och med Windows PowerShell 3.0, sparas beständig användarhanterade sessioner (”flertal PSSessions”) som du skapar med hjälp av cmdleten New-PSSession på fjärrdatorn. De är inte längre beroende av sessionen där de skapades.

Du kan nu koppla från en session utan att störa de kommandon som körs i sessionen. Du kan stänga sessionen och stänga av datorn. Senare, kan du återansluta till sessionen från en annan session på samma eller på en annan dator.

Den **ComputerName** -parametern för den [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) nu hämtar alla användarsessioner som ansluter till datorn, även om de startades i en annan session på en annan dator. Du kan ansluta till sessioner, hämta kommandonas resultat, starta nya kommandon och sedan koppla från sessionen.

Nya cmdletar har lagts till stöd för funktionen kopplas från sessioner, inklusive [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), och ta emot-PSSession och nya parametrar har lagts till cmdletar som hanterar flertal PSSessions, till exempel den **InDisconnectedSession** -parametern för den [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.

Funktionen kopplas från sessioner stöds endast när datorerna på både käll-(”klient”) och avslut (”server”) ändar av anslutningen kör Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Robust Session anslutning

Windows PowerShell 3.0 identifierar oväntat förluster för anslutningen mellan klienten och servern och försöker återupprätta anslutningen och körningen återupptas. Om klient-server-anslutningen inte kan återskapas inom den tilldelade tiden, meddelas användaren och kopplas sessionen. Vid försök att ansluta igen, ger Windows PowerShell kontinuerlig feedback till användaren.

Om en frånkopplad session har startats med hjälp av InvokeCommand, skapar ett jobb för en frånkopplad session att göra det enklare att återansluta och återuppta körning i Windows PowerShell.

De här funktionerna ger en mer tillförlitlig och återställningsbara fjärrkommunikationsupplevelse och kan användarna utföra tidskrävande uppgifter som kräver robust sessioner, till exempel arbetsflöden.

### <a name="updatable-help-system"></a>Uppdateringsbar hjälpsystem

Du kan nu hämta uppdaterade filer för cmdlets i modulerna. Den [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdleten identifierar de senaste hjälpfilerna, laddar ned dem från Internet, har packats upp dem, verifierar dem och installerar dem i rätt katalog för språkspecifika för modulen.

Om du vill använda de uppdaterade filerna, skriver du `Get-Help`. Du behöver inte starta om Windows eller Windows PowerShell. Om du vill uppdatera hjälp för moduler i katalogen $pshome, starta Windows PowerShell med alternativet ”Kör som administratör”.

Stöd för användare som inte har tillgång till Internet och användare bakom brandväggar, den nya [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet hämtar hjälpfiler till en katalog i filsystemet, till exempel en filresurs. Användarna kan sedan använda den [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet för att hämta uppdaterade filer från filresursen.

Du kan använda den [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet för att uppdatera hjälp filer för alla eller specifika moduler i alla stöds Användargränssnittet kulturer. Du kan även ange en [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) i din profil för Windows PowerShell. Som standard hämtar Windows PowerShell hjälpfilerna för en modul högst en gång om dagen.

Windows 8 och Windows Server 2012 moduler omfattar inte hjälpfiler. Om du vill hämta de senaste hjälpfilerna skriver `Update-Help`. Mer information skriver du in `Get-Help` (utan parametrar) eller se [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

När hjälpfilerna för en cmdlet inte är installerade på datorn, den [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet visar nu automatiskt genererade hjälp. Den automatisk genererade hjälpen innehåller kommandosyntax och anvisningar för att använda den [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) hämta hjälpfiler.

Alla modulägaren stödja uppdateringsbar hjälp för sina modulen. Du kan inkludera hjälpfiler i modulen och använder uppdateringsbar hjälp för att uppdatera dem eller utelämna hjälpfilerna och använda uppdateringsbar hjälp för att installera dem. Läs mer om att stödja uppdateringsbar hjälp [stöd för uppdateringsbar hjälp](https://go.microsoft.com/FWLink/?LinkID=242129) i MSDN.

### <a name="enhanced-online-help"></a>Förbättrad onlinehjälp

Direkthjälpen för Windows PowerShell är en värdefull resurs för alla användare, men det är särskilt viktigt för användare som inte vill eller kan inte installera uppdaterade filer.

Om du vill få hjälp online för alla Windows PowerShell-cmdletar, skriver du:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell öppnar onlineversionen av hjälpavsnittet i din standardwebbläsare.

Den **Get-Help-Online** funktion i Windows PowerShell 3.0 är nu ännu mer kraftfulla eftersom den fungerar även när hjälpfilerna för cmdlet: en är inte installerade på datorn. Den **Get-Help-Online** funktionen hämtar URI för onlinehjälpavsnittet från HelpUri-egenskapen för cmdletar och avancerade funktioner.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

Från och med Windows PowerShell 3.0, författare till C# cmdlets kan fylla i den **HelpUri** egenskapen genom att skapa en **HelpUri** attribut i cmdlet-klassen. Författare till avancerade funktioner kan definiera en **HelpUri** egenskap på den **CmdletBinding** attribut. Värdet för den **HelpUri** egenskapen måste börja med ”http” eller ”https”.

Du kan även inkludera en **HelpUri** värde i den första relaterad länken i en XML-baserade cmdlet-hjälpfilen eller. Länk-direktiv av kommentarbaserad hjälp i en funktion.

Läs mer om att stödja onlinehjälp [stödja onlinehjälp](/powershell/developer/module/supporting-online-help) i Microsoft-Docs.

### <a name="cim-integration"></a>CIM-integrering

Windows PowerShell 3.0 innehåller stöd för vanliga Information Model (CIM), som ger gemensamma definitioner av hanteringsinformation för system, nätverk, program och tjänster, så att de utbyte av hanteringsinformation mellan heterogena system. Stöd för CIM i Windows PowerShell 3.0, inklusive möjligheten att skapa Windows PowerShell-cmdletar baserade på nytt eller befintligt CIM klasser, kommandon utifrån cmdlet definition XML-filer, stöd för CIM .NET Framework. API: et, CIM-cmdletar för hantering och WMI 2.0-leverantörer.

### <a name="session-configuration-files"></a>Konfigurationsfiler för session

Från och med Windows PowerShell 3.0 kan utforma du en anpassad sessionskonfiguration genom att använda en fil. Konfigurationsfilen ny session kan du bestämma sessioner som använder sessionskonfigurationen, inklusive vilka moduler, skript, miljö och filer läses in i sessioner, vilka cmdlets och språk element-användare kan använda, vilka moduler och skript som de kan köras och vilka variabler som de kan se.

Du kan utforma en session där användare kan endast köra cmdletarna från en viss modul eller en session där användarna har fullständig språk, åtkomst till alla moduler och åtkomst till skript som utför avancerade uppgifter.

I tidigare versioner av Windows PowerShell kontroll på den här nivån var tillgänglig endast för de som kan skriva en C# program eller ett skript för komplex start. Nu kan kan alla medlemmar i gruppen Administratörer på datorn Anpassa en sessionskonfiguration med hjälp av en konfigurationsfil.

Du kan skapa en konfigurationsfil för sessionen med den [New PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. Tillämpa konfigurationsfilen session till en sessionskonfiguration genom att använda den [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) eller [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdletar.

Mer information finns i [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) och [New PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Schemalagda jobb och uppgiften Scheduler-integrering

Nu kan du schemalägga Windows PowerShell-bakgrundsjobb och hantera dem i Windows PowerShell och i Schemaläggaren.

Windows PowerShell schemalagda jobb är en användbar hybrid av Windows PowerShell-bakgrundsjobb och aktiviteter i Schemaläggaren.

T.ex. Windows PowerShell-bakgrundsjobb, schemalagda jobb körs asynkront i bakgrunden. Instanser av schemalagda jobb som har slutförts kan hanteras genom att använda job-cmdlets som [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) och [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Du kan köra schemalagda jobb på en gång eller återkommande schema eller som svar på en åtgärd eller händelse som aktiviteter i Schemaläggaren. Du kan visa och hantera schemalagda jobb i Schemaläggaren, aktivera och inaktivera dem efter behov, kör dem eller använda dem som en mall och ange villkor som jobbet börjar.

Dessutom kommer schemalagda jobb med en anpassad uppsättning cmdletar för att hantera dem. Cmdletarna kan du skapa, redigera, hantera, inaktivera och återaktivera schemalagda jobb, Skapa utlösare för schemalagda jobb och ange jobbalternativ för schemalagda.

Mer information om schemalagda jobb finns i [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Förbättringar i Windows PowerShell-språket

Windows PowerShell 3.0 innehåller många funktioner som är utformade för att se dess språk enklare, lättare att använda och för att undvika vanliga fel. Förbättringarna innefattar egenskapen uppräkning, antal och längd egenskaper på skalära objekt, nya omdirigeringsoperatorer, omfångsändraren $Using, PSItem automatisk variabel, flexibel skriptet formatering, attribut för variabler, förenklad attribut argument, numeriska kommandonamn, Stop-parsning operator, förbättrad matris-ihopbuntning, nya bitars operatorer, ordnad ordlistor, PSCustomObject omvandling och förbättrad kommentarbaserad hjälp.

### <a name="new-core-cmdlets"></a>Ny Kärncmdletar

Nya cmdletar har lagts till i Windows PowerShell Core-installationen, inklusive cmdlet: ar för att hantera schemalagda jobb frånkopplade sessioner, CIM-integration och uppdateras hjälpsystemet.

|||
|-|-|
|Add-JobTrigger|Ny JobTrigger|
|Connect-PSSession|New-PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|New-PSWorkflowExecutionOption|
|Inaktivera JobTrigger|Ny PSWorkflowSession|
|Disable-ScheduledJob|New-ScheduledJobOption|
|Koppla från PSSession|Ny-WinEvent|
|Enable-JobTrigger|Ta emot PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Importera IseSnippet|Set-ScheduledJobOption|
|Anropa AsWorkflow|Visa kommando|
|Invoke-CimMethod|Visa ControlPanelItem|
|Invoke-RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|Ny CimInstance|Unblock-File|
|Ny-CimSession|Unregister-ScheduledJob|
|New-CimSessionOption|Update-Help|
|Ny IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Förbättringar av befintliga Core-Cmdlets och Providers

Windows PowerShell 3.0 innehåller nya funktioner för befintliga cmdlets inklusive förenklad syntax och nya parametrar för följande cmdletar: Dator-cmdletar, CSV-cmdlet: ar, Get-ChildItem, Get-Command, Get-innehåll, Get-historik, mått-objekt, Security cmdlet: ar, Select-Object, Välj sträng, dela sökväg, startprocessen, Tee-objekt, Test-Connection, Lägg till medlem och WMI-cmdletar.

Windows PowerShell-providers har också förbättrats avsevärt, inklusive stöd för provider-certifikat för att hantera certifikat för Secure Socket Layer (SSL) för Internet, stöd för autentiseringsuppgifter, beständig nätverksenheter och alternativa dataströmmar i filsystem enheter.

### <a name="remote-module-import-and-discovery"></a>Remote modulimport och identifiering

Windows PowerShell 3.0 utökar modulidentifiering, importerar och implicit fjärrkommunikation funktioner på fjärrdatorer. Modul-cmdlet: ar hämta moduler på fjärrdatorer och importera modulerna till fjärrdatorer eller lokala datorn med hjälp av Windows PowerShell-fjärrkommunikation. Stöd för nya CIM-session kan du använda CIM- och WMI för att hantera icke-Windows-datorer genom att importera kommandon till den lokala datorn som kör implicit på fjärrdatorn.

Mer information finns i hjälpavsnitt för de [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) och [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdletar.

### <a name="enhanced-tab-completion"></a>Förbättrad Tabbifyllning

Tabbifyllning i Windows PowerShell-konsolen nu är du klar namnen på cmdletar, parametrar, parametervärden, uppräkningar, .NET Frameworks typer, COM-objekt, dolda kataloger och mer. Funktionen fliken slutförande skrivs om helt baserat på en ny parser och abstrakt syntax trädet om du vill stödja flera scenarier, till exempel InMemory-parsning träd och mittlinjen tabbifyllning.

### <a name="module-auto-loading"></a>Modulen automatisk inläsning

Den [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet nu hämtar alla cmdletar och funktioner från alla moduler som är installerade på datorn, även om modulen inte har importerats till den aktuella sessionen.

När du får den cmdlet som du behöver kan använda du det omedelbart utan att importera alla moduler. Windows PowerShell-moduler importeras nu automatiskt när du använder en cmdlet i modulen. Du behöver inte längre att söka efter modulen och importera den för att använda dess cmdletar.

Automatisk import av moduler utlöses med hjälp av cmdlet: en i ett kommando körs **Get-Command** för en cmdlet utan jokertecken eller som kör [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) för en cmdlet utan jokertecken.

Du kan aktivera, inaktivera och konfigurera automatisk import av moduler med hjälp av den **$PSModuleAutoLoadingPreference** inställningsvariabeln.

Mer information finns i [about_Modules](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [about_Preference_Variables [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b), och hjälpavsnitt för de [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) och [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdletar.

### <a name="module-experience-improvements"></a>Modulen Upplevelseförbättringar

Windows PowerShell 3.0 ger avancerade funktioner som stöds för moduler, inklusive följande nya funktioner.

1. Modulen loggning för enskilda moduler (LogPipelineExecutionDetails) och nya ”aktivera på modulen loggning” gruppolicy-inställningen
2. Utökad modul-objekt som visar värden från modulmanifestet
3. Ny **ExportedCommands** egenskapen för moduler, inklusive kapslade moduler, som kombinerar kommandon av alla typer
4. Förbättrad identifiering av tillgängliga (icke importerade) moduler, inklusive så att den **sökväg** och **ListAvailable** parametrar i samma kommando
5. Ny **DefaultCommandPrefix** nyckeln i modulmanifest som undviker namnkonflikter utan att ändra koden i modulen.
6. Förbättrad modulen krav, inklusive fullständiga nödvändiga moduler med version och GUID och automatisk import av moduler som krävs
7. Lugnare, effektiv drift av den [New ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.
8. Ny **modulen** parametern för #Requires
9. Förbättrad [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet med både **MinimumVersion** och **RequiredVersion** parametrar.

### <a name="simplified-command-discovery"></a>Förenklad kommandot identifiering

Du behöver inte längre att importera alla moduler för att identifiera kommandona som är tillgängliga i sessionen. I Windows PowerShell 3.0, den [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet hämtar alla kommandon från alla installerade moduler. Och om du använder ett kommando som exporterar kommandot modul importeras automatiskt i sessionen.

Den nya [visningskommandot](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet är särskilt utformad för nybörjare. Du kan söka efter kommandon i ett fönster. Du kan visa alla kommandon eller filtrera efter modul, importera en modul genom att klicka på en knapp, använda textrutor och listrutor för att konstruera ett giltigt kommando och sedan kopiera eller kör kommandot utan att behöva lämna fönstret.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Förbättrad loggning, diagnostik och stöd för grupper i principen

Windows PowerShell 3.0 förbättrar loggning och spårning av stöd för kommandon och moduler med stöd för händelsespårning i loggarna för Windows (ETW), en redigerbara **LogPipelineExecutionDetails** egenskapen för moduler och ”aktivera på modulen ”Loggningsgrupp principinställning. Nu kan du få parametervärden från logginformation genom att visa loggegenskaperna.

### <a name="formatting-and-output-improvements"></a>Formatering och förbättringar av utdata

Nya formateringen och utdata förbättringar förbättra effektiviteten för alla användare av Windows PowerShell. Förbättringarna innefattar omdirigering av utdata för alla strömmar, en förbättrad uppdateringstyp cmdlet som lägger till typer dynamiskt utan Format.ps1xml filer, automatiskt radbyte i utdata, standard formateringsegenskaper med anpassade objekt, den **PSCustomObject** typ, förbättrad formatering för WMI-objekt och heterogena objekt och stöd för identifiering av metoden överlagringar.

### <a name="enhanced-console-host-experience"></a>Förbättrad värd-Webbkonsol

Värdprogram för Windows PowerShell-konsolen har nya funktioner i Windows PowerShell 3.0 inklusive enkeltrådade som standard. Det nya alternativet ”Kör med PowerShell” i Utforskaren kan du köra skript i en obegränsad session genom att högerklicka på. Nya konsolen värd starta logiken startar Windows PowerShell snabbare och nya teckensnitt gör att du kan anpassa den välbekanta konsol fönstret upplevelsen.

Mer information finns i [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Ny Cmdlet och som är värd för API: er

Den nya Cmdlet-API och som är värd för API: et innehåller offentliga avancerad syntax-träd (AST) API: er och API: er för pipeline-växling, kapslade pipelines, runspace pooler tabbifyllning, Windows RT, föråldrad cmdlet-attributet och Verb och substantiv egenskaper för objektet FunctionInfo.

### <a name="performance-improvements"></a>Prestandaförbättringar

Betydande prestandaförbättringar i Windows PowerShell som kommer från den nya språk-parsern som bygger på dynamiska Runtime språk (DLR) i .NET Framework 4., tillsammans med runtime skriptet kompilering, motorn tillförlitlighet förbättringar och ändringar i den algoritmen i [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) som förbättra prestanda, särskilt när de söker nätverket delar.

### <a name="runas-and-shared-host-support"></a>Kör och stöd för delade värd

Windows PowerShell 3.0 har stöd för RunAs-och delade värden.

Den *RunAs* funktion, utformad för Windows PowerShell-arbetsflöde, kan användare av en sessionskonfiguration skapa sessioner som körs med behörigheten för ett delat användarkonto. Detta gör att mindre privilegierade användare att köra kommandon och skript med administratörsbehörighet och minskar behovet av att lägga till mindre erfarna användare i gruppen Administratörer.

Den **SharedHost** funktionen kan flera användare på flera datorer att ansluta till en Arbetsflödessession samtidigt och övervaka förloppet för ett arbetsflöde. Användare kan starta ett arbetsflöde på en dator och sedan ansluta till sessionskonfigurationen för arbetsflödet på en annan dator utan att koppla från sessionen från den ursprungliga datorn. Användare måste ha samma behörigheter och använda samma sessionskonfiguration. Mer information finns i ”som kör ett Windows PowerShell-arbetsflöde” i komma igång med Windows PowerShell-arbetsflöde.

### <a name="special-character-handling-improvements"></a>Förbättringar för hantering av specialtecken

Att förbättra möjligheten för Windows PowerShell 3.0 att tolka och hanterar specialtecken, den **LiteralPath** parametern, som hanterar specialtecken i sökvägar som är giltig för nästan alla cmdletar som har en  **Sökvägen** parameter, inklusive den nya [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) och [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdletar. Parsern innehåller också särskilda logik för att förbättra hanteringen av tecknet backtick (\`) och hakparenteser i filnamn och sökvägar.

## <a name="see-also"></a>Se även

- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
