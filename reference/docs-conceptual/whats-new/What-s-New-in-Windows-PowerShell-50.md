---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Vad är nytt i Windows PowerShell 5.0"
ms.openlocfilehash: 3a412b35c593c99fb8ea8307b12ccc05871863f4
ms.sourcegitcommit: e2360ac94fe4deb0ed0f5c8c8d9b293551ec8030
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/05/2017
---
# <a name="whats-new-in-windows-powershell-50"></a>Vad är nytt i Windows PowerShell 5.0
Windows PowerShell 5.0 innehåller nya viktiga funktioner som utökar användningen, förbättrar dess användbarhet och gör att du kan styra och hantera Windows-baserade miljöer enklare och mer omfattande.

Windows PowerShell 5.0 är bakåtkompatibel. Cmdlets, providers, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 4.0, Windows PowerShell 3.0 och Windows PowerShell 2.0 vanligtvis fungerar i Windows PowerShell 5.0 utan ändringar.

# <a name="installing-windows-powershell"></a>Installera Windows PowerShell
Windows PowerShell 5.0 installeras som standard på Windows Server 2016 Technical Preview och Windows 10. 

Om du vill installera Windows PowerShell 5.0 på Windows Server 2012 R2, Windows 8.1 Enterprise eller Windows 8.1 Pro, hämta och installera [Windows Management Framework 5.0](http://aka.ms/wmf5download). Glöm inte att läsa hämta information och uppfyller alla systemkrav, innan du installerar Windows Management Framework 5.0.

## <a name="in-this-topic"></a>I det här avsnittet

- [Windows PowerShell 4.0 DSC-uppdateringar i KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nya funktioner i Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nya funktioner i Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nya funktioner i Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Uppdateringar för Windows PowerShell 4.0 i November 2014-uppdateringen (KB 3000850)
Många uppdateringar och förbättringar för Windows PowerShell önskad tillstånd Configuration (DSC) i Windows PowerShell 4.0 finns i den [Samlad uppdatering för Windows RT 8.1, Windows 8.1 och Windows Server 2012 R2 i November 2014](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). Du kan fastställa om KB 3000850 är installerad på datorn genom att köra `Get-Hotfix -Id KB3000850` i Windows PowerShell.

- Uppdateringar av befintliga cmdletar i den [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modul

    -   [Get-DscResource](http://technet.microsoft.com/library/dn521625.aspx) är snabbare (särskilt i ISE).

    -   [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) har en ny parameter - UseExisting, som återställer senast tillämpade konfiguration.

    -   [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) -Force har korrigerats.

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) visar mer användbar information om tillståndet motorn.

    -   [Testa DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) nu Returnerar namnet på datorn tillsammans med True eller False.

    -   [Nya DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) har nu stöd för UNC-sökvägar.

- Nya cmdletar i den [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modul

    -   [Uppdatera DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx): utför en pull begäran server-kontroll.

    -   [Stoppa DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx): stoppar en konfiguration som redan körs.

    -   [Ta bort DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx): låter dig ta bort konfigurationsdokument i olika steg (väntande, tidigare eller aktuella).

- Förbättringar av språk

    -   DependsOn har nu stöd för sammansatt resurser.

    -   DependsOn stöder nu siffror i resursen instansnamn.

    -   Noduttryck som utvärderas till tom längre utlösa fel.

    -   Ett fel som uppstår om ett nod-uttryck som utvärderas som tom har korrigerats.

    -   Konfigurationer som anropar konfigurationer nu fungerar i Windows PowerShell-konsolen.

- Förbättringar av pull-läge

    -   Pull-läge stöder nu alla ZIP-filer.

    -   **AllowModuleOverwrite** fungerar nu korrekt.

- Återhämtning förbättringar

    -   Nya **DebugMode** kan du läsa resurs moduler.

    -   Om det inträffar ett fel i konfiguration, tas pending.mof-filen inte bort.

    -   Den lokala Configuration Manager (MGM) är nu mer robust när metakonfigurationen inställningar har skadats.

- Förbättringar av diagnostik

    -   En varning visas när MGM anger timern till andra inställningar än vad du har angett.

    -   Felloggarna innehåller nu anropsstacken för Windows PowerShell-resurser.

- Flexibilitet förbättringar

    -   LocalConfigurationManager resursen har en ny egenskap **ActionAfterReboot**.

        -   ContinueConfiguration (standardvärdet): återupptar en konfiguration automatiskt när en målnod har startats om.

        -   StopConfiguration: Inte automatiskt att återuppta en konfiguration, när en nod startas om.

    -   Kör en konsekvenskontroll kan nu oftare än en PULL-åtgärd eller vice versa.

    -   Stöd för versionshantering: DSC kan nu identifiera ett dokument som skapades på en nyare klient (ingår i [WMF 5.0](http://aka.ms/wmf5download)).

- Fel förebyggande förbättringar

    -   Modulversion har nu verkställts innan en konfiguration tillämpas.

    -   **DebugPreference** är nu korrekt för Get-, Set- eller Test TargetResource anrop.

- Autentiseringsuppgifter som hanterar förbättringar

    -   Ett certifikat används nu om båda **certifikat** och **PSDscAllowPlainTextPassword** har angetts.

    -   Autentiseringsuppgifter dekrypteras, även för Get-TargetResource.

    -   Metakonfigurationen autentiseringsuppgifterna krypteras och dekrypteras.

    -   PSCredentials nu dekrypteras när de inbäddade objekt.

- Förbättringar av inbyggda resurs

    -   Resursen paketet

        -   Installerar inte längre fel paketet (antingen från lokala eller källor).

        -   Har nu stöd för HTTPS.

    -   Det finns nu stöd för HTTPS i den [paketet resurs](http://technet.microsoft.com/library/dn282132.aspx).

    -   [Arkivera resurs](http://technet.microsoft.com/library/dn249917.aspx) stöder nu autentiseringsuppgifter.

## <a name="new-features-in-windows-powershell-50"></a>Nya funktioner i Windows PowerShell 5.0

- [Nya funktioner i Windows PowerShell](#new-features-in-windows-powershell)
- [Nya funktioner i Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nya funktioner i Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nya funktioner i Windows PowerShell-webbtjänster](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Viktiga felkorrigeringar i Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nya funktioner i Windows PowerShell

- Från och med Windows PowerShell 5.0, kan du utveckla med hjälp av klasser, formella syntax och semantik som liknar andra objektorienterad programmeringsspråk. **Klassen**, **Enum**, och andra nyckelord har lagts till Windows PowerShell-språk för att stödja den nya funktionen. Mer information om hur du arbetar med klasser finns i about_Classes.

- Windows PowerShell 5.0 introducerar en ny, strukturerade information dataström som du kan använda för att överföra strukturerade data mellan ett skript och dess anropare (värdmiljön). Du kan nu använda Write-värden för att generera utdata till dataströmmen information. Information dataströmmar fungerar även för PowerShell.Streams, jobb, schemalagda jobb och arbetsflöden. Följande funktioner stöder information dataströmmen.

    -   En ny cmdlet i Write-Information som du kan ange hanteringen av information dataströmmen data för ett kommando i Windows PowerShell. Skriv värden är en Omslutning för Write-Information. Skriv-Information är också en arbetsflödesaktivitet som stöds.

    -   Två nya allmänna parametrar, InformationVariable och InformationAction, kan du avgöra hur informationsströmmar från ett kommando ska visas. Giltiga värden för InformationAction är SilentlyContinue, stoppa, Fortsätt, Inquire, Ignorera eller pausa med SilentlyContinue som standard. InformationVariable anger en sträng som namn på en variabel som du vill skriva värden data från ett kommando som sparats.

    -   En ny inställningsvariabeln InformationPreference, anger din standardprioritet för information dataströmmen data i Windows PowerShell-sessionen. Standardvärdet är SilentlyContinue.

    -   Två nya arbetsflödets gemensamma parametrar, PSInformation och InformationAction, har lagts till.

    -   När du använder kommandot Format-Table formateras tabellkolumner nu automatiskt genom att utvärdera den första 300ms som passerar genom dataströmmen.

- I samarbete med [Microsoft Research](http://research.microsoft.com/), en ny cmdlet ConvertFrom-sträng, har lagts till. ConvertFrom sträng kan du extrahera och parsa strukturerade objekt från innehållet i textsträngar. Mer information finns i ConvertFrom-sträng.

- En ny konvertera strängen cmdlet formateras text baserat på ett exempel som du anger i en - exempel-parameter.

- En ny modul, Microsoft.PowerShell.Archive, innehåller cmdletar som kan du komprimera filer och mappar i (även kallat ZIP) arkivfiler, extrahera filerna från befintliga ZIP-filer och uppdatera ZIP-filer med nyare versioner av filer som komprimerats i dem.

- En ny modul, PackageManagement, kan du identifiera och installera programvarupaket på Internet. Modulen PackageManagement (kallades tidigare OneGet) är en manager eller multiplexor över den befintliga paket hanterare (kallas även paketet providers) till en mer enhetlig hantering av Windows-paketet med ett enda Windows PowerShell-gränssnitt.

- En ny modul, PowerShellGet, kan du söka efter, installera, publicera och uppdatera moduler och DSC-resurser på den [PowerShell-galleriet](http://www.powershellgallery.com/), eller på en intern modul-databasen som du kan ställa in genom att köra cmdleten Register-PSRepository.

- Ett nytt språk nyckelord **Hidden**, har lagts till att ange en medlem (en egenskap eller en metod) inte visas som standard i resultatet för Get-medlem (om du lägger till parametern - Force). Egenskaper och metoder som har markerats som dolt också visas inte i IntelliSense resultat om du inte är i ett sammanhang där medlemmen ska vara synliga. till exempel automatiska variabeln $detta ska visa dolda medlemmar i klassmetoden.

- Nytt objekt, ta bort objektet och Get-ChildItem har förbättrats för att kunna skapa och hantera [symboliska länkar](http://en.wikipedia.org/wiki/Symbolic_link). Den **- ItemType** parametern för det nya objektet accepterar ett nytt värde **SymbolicLink**. Du kan nu skapa symboliska länkar i en enda rad genom att köra cmdlet New-objektet.

- Get-ChildItem har också en ny - djup parametern, som du använder med parametern - Recurse för att begränsa rekursion. Till exempel Get-ChildItem-Recurse - djup 2 returnerar resultat från den aktuella mappen alla underordnade mappar i den aktuella mappen och alla mappar i underordnat mappar.

- Nu kan du kopiera filer och mappar från en Windows PowerShell-session till en annan, vilket innebär att du kan kopiera filer till sessioner som är anslutna till fjärrdatorer, kopiera-objekt (inklusive datorer som kör [Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), och Därför har inga andra interface). Om du vill kopiera filer, ange PSSession-ID som värde för de nya - FromSession och ToSession - parametrarna, och Lägg till - sökväg och - mål för att ange sökväg och ett mål, respektive. Till exempel kopiera objekt-sökvägen c:\\minfil.txt - ToSession $s-mål d:\\destinationFolder.

- Windows PowerShell skrivfel har förbättrats för att tillämpa alla värdbaserade program (till exempel Windows PowerShell ISE) utöver konsolen värden (**powershell.exe**). Skrivfel alternativ (inklusive att aktivera en systemomfattande betyg) kan konfigureras genom att aktivera den **aktivera PowerShell skrivfel** gruppolicy-inställningen finns i administrativa mallar/Windows komponenter/Windows PowerShell.

- En nyhet i detaljerat skript spårning kan du aktivera detaljerad spårning och analys av Windows PowerShell scripting används på ett system. När du aktiverar spårning detaljerat skript, Windows PowerShell loggar alla skriptblock händelseloggen händelsespårning för Windows ETW (Event) **Microsoft-Windows-PowerShell/Operational**.

- Från och med Windows PowerShell 5.0, nya Cryptographic Message Syntax cmdlets stöder kryptering och dekryptering av innehåll med format för IETF-standard för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](http://tools.ietf.org/html/rfc5652). Get-CmsMessage och skydda CmsMessage Unprotect CmsMessage cmdletar har lagts till i [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) modul.

- Nya cmdletar i den [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modul, Get-Runspace, Debug Runspace, Get-RunspaceDebug, RunspaceDebug aktivera och inaktivera RunspaceDebug låter dig ange felsökningsalternativ på en körningsutrymme och start och stopp Felsökning på en runspace. För felsökning av godtycklig körningsutrymmen ”som är körningsutrymmen som inte är standard runspace för en Windows PowerShell-konsol eller Windows PowerShell ISE session'” Windows PowerShell kan du ange brytpunkter i ett skript och lagt till brytpunkter Stoppa skriptet från körs innan du kan koppla en felsökare felsöka runspace skript. Kapslade felsökning stöd för valfri körningsutrymmen har lagts till felsökningsprogram för Windows PowerShell-skript för körningsutrymmen.

- En ny cmdlet i hexadecimalt Format har lagts till i [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modul. Hexadecimalt format kan du visa text eller binära data i hexadecimalt format.

- Urklipp get och Set-Urklipp cmdletar har lagts till i [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modul, de underlättar överföringen av innehåll till och från en Windows PowerShell-session. Cmdlet: ar för Urklipp stöder bilder, ljudfiler, fillistor och text.

- En ny cmdlet Rensa RecycleBin har lagts till i [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) modul; den här cmdlet förbrukade återvinningen Bin för en fast enhet som innehåller externa enheter. Som standard uppmanas du att bekräfta kommandot Rensa RecycleBin eftersom egenskapen ConfirmImpact för cmdlet har angivits för ConfirmImpact.High.

- En ny cmdlet New-TemporaryFile, kan du skapa en temporär fil som en del av skript. Som standard skapas den nya tillfälliga filen i ```C:\Users\<user name>\AppData\Local\Temp```.

- Out-File, Lägg till innehåll och ange innehåll cmdlets nu har en ny NoNewline - parameter som utelämnar en ny rad efter utdatan.

- Cmdlet New-Guid utnyttjar .NET Framework Guid-klassen för att generera ett GUID-användbart när du skriver skript eller DSC-resurser.

- Eftersom filversionsinformation kan vara vilseledande, särskilt när en fil är skyddad, är nya FileVersionRaw och ProductVersionRaw skriptegenskaper tillgängliga för FileInfo objekt. Du kan till exempel köra följande kommando för att visa värdena i de här egenskaperna för powershell.exe, där $pid innehåller process-ID för en session som körs i Windows PowerShell:```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```

- Nya cmdletar RETUR PSHostProcess och avsluta PSHostProcess kan du felsöka Windows PowerShell-skript i processer som är separat från den aktuella processen körs i Windows PowerShell-konsolen. Kör RETUR-PSHostProcess om du vill ange eller ansluta till en specifik process-ID och kör sedan Get-Runspace för att returnera active körningsutrymmen inom processen. Kör avsluta PSHostProcess frånkoppling från processen när du är klar felsökning av skript i processen.

- En ny cmdlet vänta felsökare har lagts till i [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modul. Du kan köra vänta felsökning om du vill stoppa en skriptet i felsökaren innan du kör instruktionen nästa i skriptet.

- Windows PowerShell-arbetsflöde felsökningsprogrammet stöder nu kommando eller fliken slutförande och du kan felsöka inkapslat arbetsflöde funktioner. Du kan nu trycka på **Ctrl + Break** ange felsökningsprogrammet i ett skript som körs i både lokala och fjärranslutna sessioner och i ett arbetsflöde för skript.

- En Debug-Job-cmdlet har lagts till i [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) modul för att felsöka skript som körs jobbet för Windows PowerShell-arbetsflöde, bakgrund och jobb som körs i fjärrsessioner.

- Tillståndet nya AtBreakpoint, har lagts till för Windows PowerShell-jobb. Skriptet har nått en brytpunkt tillståndet AtBreakpoint gäller när ett jobb körs ett skript som innehåller ange brytpunkter. När ett jobb har stoppats på en brytpunkt debug, måste du felsöka jobbet genom att köra cmdleten Debug-Job.

- Windows PowerShell 5.0 implementerar stöd för flera versioner av en enda Windows PowerShell-modulen i samma mapp i $PSModulePath. En RequiredVersion-egenskap har lagts till klassen ModuleSpecification för att du får den önskade versionen av en modul; den här egenskapen är ömsesidigt uteslutande med egenskapen ModuleVersion. RequiredVersion stöds nu som en del av värdet för parametern FullyQualifiedName Get-modulens Import-Module och ta bort modulen cmdlets.

- Du kan nu utföra modulen version verifiering genom att köra cmdleten Test-ModuleManifest.

- Resultaten av cmdleten Get-Command nu visas i versionskolumnen; en ny Version-egenskap har lagts till CommandInfo-klassen. Get-Command visar kommandon från flera versioner av samma modul. Egenskapen Version ingår också i härledda klasser för CmdletInfo: CmdletInfo och ApplicationInfo.

- Get-Command har en ny parameter - ShowCommandInfo, som returnerar information om ShowCommand PSObjects. Detta är särskilt användbar funktion för när Visa kommando körs i Windows PowerShell ISE med hjälp av Windows PowerShell-fjärrkommunikation. Ersätter befintlig Get-SerializedCommand-funktion i modulen Microsoft.PowerShell.Utility för parametern - ShowCommandInfo, men skriptet Get-SerializedCommand är fortfarande tillgängliga till stöd för äldre skript.

- En ny cmdlet Get-ItemPropertyValue kan du hämta värdet för en egenskap utan med hjälp av punktnotation. I äldre versioner av Windows PowerShell kan du exempelvis kör följande kommando för att hämta värdet för egenskapen Programbas för registernyckeln PowerShellEngine: **(Get-ItemProperty-sökvägen HKLM:\\programvara\\ Microsoft\\PowerShell\\3\\PowerShellEngine-Name ApplicationBase). ApplicationBase**. Från och med Windows PowerShell 5.0, kan du köra **ItemPropertyValue Get-sökvägen HKLM:\\programvara\\Microsoft\\PowerShell\\3\\PowerShellEngine-namnet ApplicationBase** .

- Windows PowerShell-konsolen använder nu syntax färger, precis som för Windows PowerShell ISE.

- En ny modul NetworkSwitch innehåller cmdletar som gör att du kan använda växeln, virtuellt LAN (VLAN) och grundläggande nivå 2-port nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar.

- Parametern FullyQualifiedName har lagts till Import-Module och ta bort modulen cmdletar för att stödja lagra flera versioner av en enskild modul.

- Save-Help, Update-Help, PSSession Import, Export-PSSession och Get-Command har en ny parameter FullyQualifiedModule av typen ModuleSpecification. Lägg till den här parametern om du vill ange en modul med ett fullständigt kvalificerat namn.

- Värdet för **$PSVersionTable.PSVersion** har uppdaterats till 5.0.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nya funktioner i Windows PowerShell Desired State Configuration

- Förbättringar i Windows PowerShell språk kan du definiera Windows PowerShell önskad tillstånd Configuration DSC ()-resurser med hjälp av klasser. Importera DscResource är nu en true dynamiska nyckelord. Windows PowerShell Parsar angiven modul '™ s rotmodul söker efter klasser som innehåller attributet DscResource. Du kan nu använda klasser för att definiera DSC-resurser, där varken en MOF-fil eller en DSCResource undermapp i mappen modul krävs. En fil för Windows PowerShell-modulen kan innehålla flera klasser i DSC-resurs.

- En ny parameter ThrottleLimit, har lagts till med följande cmdlets i modulen PSDesiredStateConfiguration. Lägg till parametern ThrottleLimit för att ange hur många datorer eller enheter som du vill att kommandot ska fungera på samma gång.

    -   Get-DscConfiguration

    -   Get-DscConfigurationStatus

    -   Get-DscLocalConfigurationManager

    -   Återställ DscConfiguration

    -   Testa DscConfiguration

    -   Jämför DscConfiguration

    -   Publicera DscConfiguration

    -   Ange DscLocalConfigurationManager

    -   Start-DscConfiguration

    -   Uppdatera DscConfiguration

- Med centraliserade DSC felrapportering är omfattande felinformation inte bara inloggad event log, men den kan skickas till en central plats för senare analys. Du kan använda den här central plats för att lagra DSC-konfigurationsfel som har inträffat för alla servrar i sina miljöer. När rapportservern har definierats i metadata-konfigurationen, alla fel skickas till rapportservern, och sedan lagras i en databas. Du kan ställa in den här funktionen oavsett om huruvida en Målnoden är konfigurerad för att hämta konfigurationer från en pull-server.

- Förbättringar av Windows PowerShell ISE underlättar redigering av DSC-resurs. Du kan nu göra följande.

    -   Visa en lista med alla DSC resurser inom en **configuration** eller **nod** block genom att ange **Ctrl + blanksteg** på en tom rad i blocket.

    -   Automatisk komplettering på resursegenskaper i den **uppräkningen** typen.

    -   Automatisk komplettering på den **DependsOn** -egenskapen för DSC-resurser, baserat på andra resurs-instanser i konfigurationen.

    -   Förbättrad flikavslutande av egenskapsvärden för resurs.

- En användare kan nu köra en resurs under en angiven uppsättning autentiseringsuppgifter genom att lägga till den **PSDscRunAsCredential** attribut i en nod-blocket. Till exempel PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Den här funktionen är användbart för att skapa konfigurationer som kör Windows Installer och körbara installationsprogram, komma åt registreringsdatafilen per användare eller utföra andra uppgifter utanför aktuellt användarsammanhang.

- stöd för 32-bitars (x86-baserat) har lagts till för den **Configuration** nyckelord.

- Windows PowerShell innehåller nu stöd för anpassad hjälp för DSC-konfigurationer som fastställs genom att lägga till \[CmdletBinding()] till funktionen genererade konfigurationen.

- En ny **DscLocalConfigurationManager** attribut anger ett block med konfigurationen som en meta-konfiguration, som används för att konfigurera DSC Local Configuration Manager. Det här attributet begränsar en konfiguration som innehåller objekt som konfigurerar DSC Local Configuration Manager. Under bearbetning av den här konfigurationen genererar en \*. meta.mof-fil som sedan skickas till lämplig målnoder genom att köra cmdlet Set-DscLocalConfigurationManager.

- Partiell konfigurationer tillåts nu i Windows PowerShell 5.0. Du kan leverera configuration dokument till en nod i fragment. För en nod att ta emot flera fragment i en konfiguration dokumentet noden '™ s Local Configuration Manager måste anges först att ange förväntade fragment

- Synkroniseringen mellan datorn är ny i DSC i Windows PowerShell 5.0. Med hjälp av inbyggda WaitFor\* resurser (**WaitForAll**, **WaitForAny**, och **WaitForSome**), kan du nu ange beroenden mellan datorer under konfigurationen körs utan externa orkestreringarna. Dessa resurser innehåller nod till nod synkronisering med hjälp av CIM-anslutningar via WS-Man-protokollet. En konfiguration kan vänta på en annan dator '™ s resurstillståndet att ändra.

- Bara tillräckligt Administration JEA (), en ny delegering säkerhetsfunktion, använder DSC och Windows PowerShell begränsade körningsutrymmen för att säkra företag från dataförlust eller röjande av anställda, om avsiktlig och oavsiktlig. Mer information om JEA, inklusive där du kan hämta xJEA DSC-resursen finns [bara tillräckligt Administration, steg-för-steg](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).

- Följande nya cmdletar har lagts till modulen PSDesiredStateConfiguration.

    -   En ny cmdlet Get-DscConfigurationStatus hämtar översiktlig information om status för konfiguration från målnoden. Du kan hämta status för senast eller för alla konfigurationer.

    -   En ny jämför DscConfiguration cmdlet jämför en angiven konfiguration med en eller flera målnoder bibliotekets tillstånd.

    -   En ny publicera DscConfiguration cmdlet kopierar en konfiguration MOF-fil till målnoden, men tillämpa inte konfigurationen. Konfigurationen tillämpas under nästa konsekvenskontroll pass eller när du kör cmdlet Update DscConfiguration.

    -   En ny DscConfiguration Test-cmdlet kan du kontrollera att en resulterande konfigurationen matchar önskad konfiguration, returnerar värdet SANT om konfigurationen matchar önskad konfiguration eller falskt om den faktiska konfigurationen inte matchar den önskade konfiguration.

    -   En ny uppdatering DscConfiguration cmdlet tvingar en konfiguration som ska bearbetas. Om den lokala Configuration Manager finns i pull-läge, hämtar cmdlet konfigurationen från hämtningsservern i innan den tillämpas.

### <a name="new-features-in-windows-powershell-ise"></a>Nya funktioner i Windows PowerShell ISE

- Du kan nu redigera fjärransluten Windows PowerShell-skript och filer i en lokal kopia av Windows PowerShell ISE genom att köra Enter-PSSession för att starta en fjärrsession på datorn som '™ s lagra filer som du vill redigera och sedan körs **PSEdit <path and file name on the remote computer>**. Den här funktionen underlättar redigera Windows PowerShell-filer som lagras på en Server Core installation av Windows Server, där Windows PowerShell ISE inte kan köras.

- Cmdleten Start-betyg stöds nu i Windows PowerShell ISE.

- Nu kan du felsöka remote skript i Windows PowerShell ISE.

- Ett nytt kommando **Bryt alla** (Ctrl + F) delar i felsökaren för både lokala och via fjärranslutning med skript.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nya funktioner i Windows PowerShell-webbtjänster (Management OData IIS Extension)

- Från och med Windows PowerShell 5.0, kan du generera en uppsättning Windows PowerShell-cmdlets baserat på de funktioner som exponeras av en viss OData-slutpunkt, genom att köra cmdleten Export-ODataEndpointProxy hittades i den nya [ Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) modul.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Viktiga felkorrigeringar i Windows PowerShell 5.0

- Windows PowerShell 5.0 innehåller en ny COM-implementering, vilket ger betydande prestandaförbättringar när du arbetar med COM-objekt. En videodemonstration av effekten finns [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ).

- Betydande prestandaförbättringar har gjorts till den första flikslutförande i en Windows PowerShell-session, förkorta fliken tid för slutförande av nästan 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nya funktioner i Windows PowerShell 4.0
Windows PowerShell 4.0 är bakåtkompatibel. Cmdlets, providers, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 3.0 och Windows PowerShell 2.0 fungerar i Windows PowerShell 4.0 utan ändringar.

Windows PowerShell 4.0 är installerad som standard i Windows 8.1 och Windows Server 2012 R2. Om du vill installera Windows PowerShell 4.0 på Windows 7 med SP1 eller Windows Server 2008 R2, hämta och installera [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Glöm inte att läsa hämta information och uppfyller alla systemkrav, innan du installerar Windows Management Framework 4.0.

- [Nya funktioner i Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nya funktioner i Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nya funktioner i Windows PowerShell-arbetsflöde](#new-features-in-windows-powershell-workflow)
- [Nya funktioner i Windows PowerShell-webbtjänster](#new-features-in-windows-powershell-web-services)
- [Nya funktioner i Windows PowerShell-webbåtkomst](#new-features-in-windows-powershell-web-access)
- [Viktiga felkorrigeringar i Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 innehåller följande nya funktioner.

### <a name="new-features-in-windows-powershell"></a>Nya funktioner i Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) är ett nytt system i Windows PowerShell 4.0 som möjliggör distribution och hantering av konfigurationsdata för programtjänster och miljön där tjänsterna körs. Läs mer om DSC [Kom igång med Windows PowerShell Desired State Configuration](https://technet.microsoft.com/en-us/library/c134aa32-b085-4656-9a89-955d8ff768d0).

- **Save-Help** nu kan du spara hjälp för moduler som är installerade på fjärrdatorer. Du kan använda Save-Help för att hämta modulen hjälp från en Internet-ansluten klient (där alla moduler som du vill ha hjälp nödvändigtvis installeras) och sedan kopiera en delad fjärrmapp eller en fjärrdator som inte har Internet sparade hjälpen åtkomst.

- Windows PowerShell-felsökaren har förbättrats för att tillåta felsökning av Windows PowerShell-arbetsflöden, samt skript som körs på fjärrdatorer. Windows PowerShell-arbetsflöden kan nu felsökas på skriptnivån från kommandoraden i Windows PowerShell eller Windows PowerShell ISE. Windows PowerShell-skript, inklusive skriptarbetsflöden, kan nu felsökas över fjärrsessioner. Felsökning fjärrsessioner bevaras via Windows PowerShell fjärrsessioner som frånkopplad och sedan återansluta senare.

- En **RunNow** parameter för **Register-ScheduledJob** och **mängd-ScheduledJob** eliminerar behovet av att ange en omedelbar startdatum och tidpunkt för jobb med hjälp av **Utlösaren** parameter.

- **Invoke-RestMethod** och **Invoke-WebRequest** nu kan du ange alla rubriker med hjälp av parametern huvuden. Även om den här parametern har alltid funnits, var en av flera parametrar för web-cmdlets som resulterade i fel eller undantag.

- **Get-Module** har en ny parameter **FullyQualifiedName**, av typen **ModuleSpecification\[]**. Den **FullyQualifiedName** parametern i Get-Module nu kan du ange en modul med hjälp av modulens namn, version och du kan också dess GUID.

- Standardinställningen för körning av principen på Windows Server 2012 R2 är **RemoteSigned**. Det finns ingen ändring i inställningen på Windows 8.1.

- Från och med Windows PowerShell 4.0, stöds metodanropet genom att använda dynamiska metodnamn. Du kan använda en variabel för att lagra ett metodnamn och dynamiskt anropa metoden genom att anropa variabeln.

- Asynkron arbetsflödesjobb är inte längre bort när tidsgränsen som anges av den **PSElapsedTimeoutSec** gemensamma arbetsflödesparametern har gått ut.

- En ny parameter **RepeatIndefinitely**, har lagts till i **New-JobTrigger** och **Set-JobTrigger** cmdlets. Detta eliminerar behovet av att ange en **TimeSpan.MaxValue** värde för den **RepetitionDuration** parametern ska upprepas ett schemalagt jobb på obestämd tid.

- En **Passthru** parametern har lagts till i **aktivera JobTrigger** och **inaktivera JobTrigger** cmdlets. Passthru-parametern visas alla objekt som skapas eller ändras av ett kommando.

- Parameternamn för att ange en arbetsgrupp i den **Add-Computer** och **Remove-Computer** cmdlets är nu konsekvent. Båda cmdlets nu använder du parametern **arbetsgruppsnamnet**.

- En ny vanliga parameter **PipelineVariable**, har lagts till. PipelineVariable kan du spara resultatet av ett via rörledningar kommando (eller en del av kommandot via rörledningar) som en variabel som kan skickas via resten av pipeline.

- Samlingen filtrering med hjälp av en metodsyntax stöds nu. Det innebär att du kan nu filtrera en uppsättning objekt med förenklad syntax som liknar för WHERE () eller Where-Object, formateras som ett metodanrop. Följande är ett exempel: (Get-Process) .where ({$_. Name - matchar ”powershell”})

- Den **Get-Process** cmdlet har en ny parameter i växeln **IncludeUserName**.

- En ny cmdlet **Get-FileHash**, som returnerar ett hash-värdet i flera olika format för en viss fil, har lagts till.

- I Windows PowerShell 4.0, om en modul använder den **DefaultCommandPrefix** nyckel i manifestet, eller om användaren importerar en modul med det **prefixet** parameter, den **ExportedCommands**egenskapen på modulen som visar kommandon i modulen med prefix. När du kör kommandona med hjälp av modulkvalificerade syntax Modulnamn\\CommandName, kommandonamn måste inkludera prefixet.

- Värdet för **$PSVersionTable.PSVersion** har uppdaterats till 4.0.

- **WHERE ()** operatorn beteende har ändrats. `Collection.Where('property -match name')`Acceptera ett stränguttryck i formatet `"Property -CompareOperator Value"` stöds inte längre. Men den **WHERE ()** operatorn accepterar stränguttryck i formatet av en scriptblock; detta förfarande fortfarande stöds.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nya funktioner i Windows PowerShell Integrated Scripting Environment (ISE)

- Windows PowerShell ISE stöder både Windows PowerShell-arbetsflöde felsökning och felsökning av fjärråtkomst skript.

- IntelliSense-stöd har lagts till för Windows PowerShell Desired State Configuration-providers och konfigurationer.

### <a name="new-features-in-windows-powershell-workflow"></a>Nya funktioner i Windows PowerShell-arbetsflöde

- Stöd har lagts till för en ny **PipelineVariable** gemensamma parametern i samband med iterativ pipelines, till exempel de som används av System Center Orchestrator; som är rörledningar som kör kommandon bara vänster till höger, inte bland kör via strömning.

- Parameterbindningen har förbättrats avsevärt för att fungera utanför fliken slutförande scenarier, såsom med kommandon som inte finns i den aktuella runspace.

- Stöd för anpassade container aktiviteter har lagts till Windows PowerShell-arbetsflöde. Om en Aktivitetsparametern är av typerna **aktiviteten**, **aktiviteten\[]**' ”eller är en allmän uppsättning aktiviteter” och användaren har angett ett skriptblock som ett argument, sedan Windows PowerShell-arbetsflöde konverterar skriptblocket till XAML, precis som med normal kompilering för Windows PowerShell-skript-arbetsflöde.

- Efter en krasch återansluter Windows PowerShell-arbetsflöde automatiskt till hanterade noder.

- Du kan nu begränsa **Foreach-Parallel** aktivitet instruktioner med hjälp av den **ThrottleLimit** egenskapen.

- Den **ErrorAction** gemensamma parametern har ett nytt giltigt värde **pausa**, som endast för arbetsflöden.

- En slutpunkt för arbetsflödet nu stängs automatiskt om det inte finns några aktiva sessioner och inga pågående jobb inga väntande jobb. Den här funktionen sparar resurser på datorn som fungerar som arbetsflödesservern, när automatisk stängning villkor är uppfyllda.

### <a name="new-features-in-windows-powershell-web-services"></a>Nya funktioner i Windows PowerShell-webbtjänster

- När ett fel uppstår i Windows PowerShell-webbtjänster (PSWS, även kallade Management OData IIS Extension), när körs en cmdlet mer detaljerade fel som returneras till anroparen. Dessutom felkoder följer [Windows Azure REST API felkod riktlinjer](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).

- En slutpunkt kan nu ange API-version, samt framtvinga användningen av en viss API-version. När det sker version matchningsfel mellan klienten och servern, visas fel för både klienten och servern.

- Hantering av dispatch-schemat har förenklats genom att automatiskt generera värden för alla fält som saknas i schemat. Generation uppstår som en bra utgångspunkt, även om dispatch-schemat inte finns.

- Typen hantering i PSWS har förbättrats för att stödja typer som använder en annan konstruktor än Standardkonstruktorn, fungerar på samma sätt som den **PSTypeConverter** i Windows PowerShell. På så sätt kan du använda komplexa typer med PSWS.

- PSWS kan nu expandera en associerad instans när du kör en fråga. Överför kostnaden är viktig för större binära innehåll (till exempel bilder, ljud eller video) och är det bättre att överföra binära data utan kodning. PSWS använder namngiven resurs dataströmmar för att överföra utan kodning. Den namngivna resursen är en egenskap för en entitet av den **Edm.Stream** typen. Varje namngivet resursström har en separat URI för GET eller UPDATE-åtgärder.

- OData-åtgärder ger nu en mekanism för att anropa metoder för icke-CRUD (skapa, läsa, uppdatera och ta bort) på en resurs. Du kan anropa en åtgärd genom att skicka en HTTP POST-begäran till URI: N som har definierats för åtgärden. Parametrar för åtgärden definieras i brödtexten för POST-begäran.

- Alla URL: er bör förenklas för att stämma överens med Windows Azure riktlinjer. En ändring som ingår i **nyckel som Segment** tillåter enda nycklar representeras segment. Observera att referenser som använder flera nyckelvärden kräver kommaavgränsade värden i parentetiska notation som tidigare.

- Innan den här versionen av PSWS, den endast sätt för att utföra skapa, uppdatera och ta bort operations var att anropa Post, Put eller ta bort på översta nivån resursen. Nytt i den här versionen av PSWS användarna finns resurs operations få samma resultat när du ansluter till samma resurs mindre direkt närmar sig som om dessa resurser fanns.

### <a name="new-features-in-windows-powershell-web-access"></a>Nya funktioner i Windows PowerShell-webbåtkomst

- Du kan koppla från och återansluter till befintliga sessioner i den webbaserade Windows PowerShell Web Access-konsolen. En **spara** knappen i den webbaserade konsolen kan du koppla från en session utan att ta bort den och återansluta till sessionen som en annan tid.

- Standardparametrar kan visas på sidan logga in. Om du vill visa standardparametrar konfigurera värden för alla inställningar som visas i den **valfria anslutningsinställningar** område på inloggningssidan i en fil med namnet **web.config**. Du kan använda den **web.config** fil att konfigurera alla valfria anslutningsinställningar utom en andra eller en annan uppsättning autentiseringsuppgifter.

- I Windows Server 2012 R2, kan du fjärrhantera auktoriseringsregler för Windows PowerShell Web Access. Den **Add-PswaAuthorizationRule** och **Test-PswaAuthorizationRule** cmdlets nu har en parameter för autentiseringsuppgifter som gör att administratörer kan hantera auktoriseringsregler från en fjärrdator eller i en Windows PowerShell Web Access-session.

- Du kan nu använda flera Windows PowerShell Web Access-sessioner i en enda webbläsarsession med hjälp av en ny webbläsarflik för varje session. Du behöver inte längre att öppna en ny webbläsarsession att ansluta till en ny session i den webbaserade Windows PowerShell-konsolen.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Viktiga felkorrigeringar i Windows PowerShell 4.0

- **Get-Counter** nu kan returnera räknare som innehåller en apostroftecknet i franska versioner av Windows.

- Nu kan du visa den **GetType** -metoden i avserialiserat objekt.

- **#Requires** instruktioner nu användarna kräver administratörsbehörighet för åtkomst, om det behövs.

- Den **importera Csv** cmdlet nu ignorerar tomma rader.

- Ett problem där Windows PowerShell ISE använder för mycket minne när du kör en **Invoke-WebRequest** kommandot har korrigerats.

- **Get-Module** visas nu modulversioner i en **Version** kolumn.

- Ta bort objekt - Recurse nu tar bort objekt från undermappar som förväntat.

- En **användarnamn** egenskapen har lagts till **Get-Process** utdata objekt.

- Den **Invoke-RestMethod** cmdlet returnerar nu alla tillgängliga resultat.

- **Lägg till medlem** nu börjar gälla på hashtabeller, även om hashtabeller som ännu inte har öppnats.

- **Select-Object - Expandera** längre misslyckas och genererar ett undantag om värdet på egenskapen är null eller tomt.

- **Get-Process** kan nu användas i en pipeline med andra kommandon som får den **ComputerName** egenskap från objekt.

- **ConvertTo Json** och **ConvertFrom Json** går nu att använda termer inom dubbla citattecken och dess felmeddelanden är nu lokaliserbara.

- **Get-Job** returnerar nu någon slutförts schemalagda jobb, även i nya sessioner.

- Problem med att montera och demontera virtuella hårddiskar med hjälp av den **FileSystem** provider i Windows PowerShell 4.0 har åtgärdats. Windows PowerShell är nu kunna identifiera nya enheter när de är monterade i samma session.

- Du behöver inte längre uttryckligen läsa in **ScheduledJob** eller **arbetsflöde** moduler för att arbeta med sina jobbtyper.

- Prestandaförbättringar har gjorts att importera arbetsflöden som definierar kapslade arbetsflöden. den här processen är nu snabbare.

## <a name="new-features-in-windows-powershell-30"></a>Nya funktioner i Windows PowerShell 3.0
Windows PowerShell 3.0 innehåller följande nya funktioner.

- [Windows PowerShell-arbetsflöde](#windows-powershell-workflow)
- [Windows PowerShell-webbåtkomst](#windows-powershell-web-access)
- [Nya funktioner i Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Stöd för Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Stöd för Windows Preinstallation Environment](#support-for-windows-preinstallation-environment)
- [Frånkopplade sessioner](#disconnected-sessions)
- [Robust Session anslutning](#robust-session-connectivity)
- [Uppdateringsbar hjälp](#updatable-help-system)
- [Förbättrad direkthjälp](#enhanced-online-help)
- [CIM-integrering](#cim-integration)
- [Konfigurationsfiler för session](#session-configuration-files)
- [Schemalagda jobb och uppgiften Scheduler-integrering](#scheduled-jobs-and-task-scheduler-integration)
- [Förbättringar i Windows PowerShell-språk](#windows-powershell-language-enhancements)
- [Ny-Kärncmdletar](#new-core-cmdlets)
- [Förbättringar av befintliga Core-Cmdlets och leverantörer](#improvements-to-existing-core-cmdlets-and-providers)
- [Remote modulimporten och identifiering](#remote-module-import-and-discovery)
- [Förbättrad Flikavslutande](#enhanced-tab-completion)
- [Modulen automatisk inläsning](#module-auto-loading)
- [Modulen upplevelse förbättringar](#module-experience-improvements)
- [Förenklad kommandot identifiering](#simplified-command-discovery)
- [Förbättrad loggning, diagnostik och stöd för principen](#improved-logging-diagnostics-and-group-policy-support)
- [Formatering och förbättringar av utdata](#formatting-and-output-improvements)
- [Förbättrad konsolen värden upplevelse](#enhanced-console-host-experience)
- [Ny Cmdlet och vara värd för API: er](#new-cmdlet-and-hosting-apis)
- [Prestandaförbättringar](#performance-improvements)
- [RunAs- och delad värdgrupp Support](#runas-and-shared-host-support)
- [Förbättringar för hantering av specialtecken](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell-arbetsflöde
Windows PowerShell-arbetsflöde ger kraften i Windows Workflow Foundation för Windows PowerShell. Du kan skriva arbetsflöden i XAML eller i Windows PowerShell-språk och köra dem på samma sätt som du vill köra en cmdlet. Den [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet hämtar workflw kommandon och [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) hämtar hjälp för arbetsflöden.

Arbetsflöden är sekvenser av multicomputer hanteringsaktiviteter som är långvariga, upprepbara, frekventa, parallell, ifrån, suspendable och kan startas om. Arbetsflöden kan återupptas från ett avsiktliga och oavsiktliga avbrott, till exempel ett nätverksavbrott, en omstart av Windows eller ett strömavbrott.

Arbetsflöden är också bärbara; de kan exporteras som eller importeras från XAML-filer. Du kan skriva anpassade sessionskonfigurationer som tillåter arbetsflöden eller aktiviteter i ett arbetsflöde körs av delegerade eller underordnade användare.

Följande är fördelarna med Windows PowerShell-arbetsflöde

- Automatisering av sekvenserade, långvariga uppgifter.

- **Fjärråtkomst övervakning av tidskrävande uppgifter**. Status och förlopp för aktiviteter är synliga när som helst.

- **Hantering av multicomputer.** Köra uppgifter samtidigt som arbetsflöden på hundratals hanterade noder. Windows PowerShell-arbetsflöde innehåller ett inbyggt bibliotek med vanliga parametrar, till exempel **PSComputerName**, som gör det möjligt för scenarier med hantering av flera datorer.

- **Enskild uppgift körning av komplexa processer.** Du kan kombinera relaterade skript som implementerar ett helt slutpunkt till slutpunkt-scenario i ett enda arbetsflöde.

- **Beständiga.** : ett arbetsflöde sparas (eller kontrollera pekar) vid specifika tidpunkter som definierats av författaren så att du kan återuppta arbetsflödet från senast sparade aktivitet (eller kontrollpunkt) i stället för att starta om arbetsflödet från början.

- **Stabilitet.** Återställning av automatisk fel. Arbetsflöden klarar planerade och oplanerade omstarter. Du kan pausa arbetsflödeskörning och återuppta arbetsflödet från den sista punkten beständiga. Arbetsflödesskapare kan ange specifika aktiviteter för att köra om fel uppstår på en eller flera hanterade noder.

- **Möjlighet att koppla från, Anslut och körs i sessionen.** Användare kan ansluta och koppla från arbetsflödesservern, men arbetsflödet körs kontinuerligt. Du kan logga ut från klientdatorn eller starta om klientdatorn och övervaka arbetsflödeskörning från en annan dator utan att avbryta arbetsflödet.

- **Schemaläggning.** Uppgifter i arbetsflödet kan schemaläggas som alla Windows PowerShell-cmdlet eller ett skript.

- **Arbetsflödet och anslutningsbegränsning.** Arbetsflödeskörning och anslutningar till noder kan vara begränsas, vilket gör att scenarier för skalbarhet och hög tillgänglighet.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access
Windows PowerShell Web Access är en funktion i Windows Server 2012 som användarna kan köra Windows PowerShell-kommandon och skript i en webbaserad konsol. Enheter som använder den webbaserade konsolen kräver inte Windows PowerShell, fjärrhanteringsprogramvara eller plugin-installationer av webbläsaren. Allt som krävs är en korrekt konfigurerad Windows PowerShell Web Access-gateway och en webbläsare som stöder JavaScript och accepterar cookies.

Mer information finns i [distribuera Windows PowerShell Web Access](http://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nya funktioner i Windows PowerShell ISE
För Windows PowerShell 3.0, Windows PowerShell Integrated Scripting Environment (ISE) har många nya funktioner, inklusive IntelliSense visar-kommandofönstret enhetlig konsolfönstret kodavsnitt, matchning klammerparentes, Visa-Dölj avsnitt, spara automatiskt, senaste objekt lista, omfattande kopia, blockera kopiering och fullständigt stöd för att skriva arbetsflöden för Windows PowerShell-skript. Mer information finns i [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/en-us/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Stöd för Microsoft .NET Framework 4
Windows PowerShell bygger mot Common Language Runtime 4.0. Cmdlet, skript och arbetsflödesskapare kan använda de nya Microsoft .NET Framework 4-klasserna i Windows PowerShell med funktioner för programkompatibilitet och distribution, hanteras utökningsbarhet Framework, parallella datoranvändning, nätverk, Windows Communication Foundation och Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Stöd för Windows Preinstallation Environment
Windows PowerShell 3.0 är en valfri komponent i Windows Preinstallation Environment (Windows PE) 4.0 för Windows 8. Windows PE är ett minimalt operativsystem som startar en dator där inget operativsystem och förbereder den för installation av Windows. Windows PE kan användas för att partitionera och formatera hårddiskar, kopiera diskavbildningar till en dator och starta installationsprogrammet för Windows från en nätverksresurs. Windows PowerShell 3.0 kan användas på Windows PE för att hantera distribution, diagnostik och återställningsscenarier.

### <a name="disconnected-sessions"></a>Frånkopplade sessioner
Från och med Windows PowerShell 3.0, sparas beständiga användarhanterat sessioner (”flertal PSSessions”) som du skapar med hjälp av cmdleten New-PSSession på fjärrdatorn. De inte längre beroende av den session där de skapades.

Du kan nu koppla från en session utan att störa de kommandon som körs i sessionen. Du kan stänga sessionen och Stäng av datorn. Senare kan du återansluta till sessionen från en annan session på samma eller en annan dator.

Den **ComputerName** parameter för den [Get-PSSession](https://technet.microsoft.com/en-us/library/b2b10531-d0df-4746-b877-e75c09955cb6) nu hämtar alla användarsessioner som ansluter till datorn, även om de startades i en annan session på en annan dator. Du kan ansluta till sessioner, Hämta resultaten av kommandon, starta nya kommandon och sedan koppla från sessionen.

Nya cmdletar har lagts till stöd för funktionen kopplas från sessioner, inklusive [Disconnect-PSSession](https://technet.microsoft.com/en-us/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/en-us/library/b803dd29-f208-4079-80d4-db04d778f060), och ta emot-PSSession och nya parametrar har lagts till cmdlets som hanterar flertal PSSessions, som den **InDisconnectedSession** parameter för den [Invoke-Command](https://technet.microsoft.com/en-us/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.

Funktionen kopplas från sessioner stöds endast när datorerna på både käll (”klient”) och avslutar (”server”) ändar av anslutningen kör Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Robust Session anslutning
Windows PowerShell 3.0 identifierar oväntat förluster för anslutningen mellan klienten och servern och försök att återupprätta anslutningen och återuppta körning automatiskt. Om klient / server-anslutningen inte kan återskapas under den tilldelade tiden, meddelas användaren och kopplas sessionen. Windows PowerShell innehåller kontinuerlig feedback till användaren vid försök att ansluta igen.

Om en frånkopplad session har startats med hjälp av InvokeCommand skapas ett jobb för en frånkopplad session att göra det enklare att återansluta och återuppta körning i Windows PowerShell.

Dessa funktioner ger en mer tillförlitlig och återställningsbara fjärrkommunikationsupplevelse och tillåta användare att utföra tidskrävande uppgifter som kräver robust sessioner, till exempel arbetsflöden.

### <a name="updatable-help-system"></a>Uppdateringsbar hjälp
Du kan nu hämta uppdaterade hjälpfilerna för cmdlets i modulerna. Den [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet identifierar de senaste hjälpfilerna, hämtas från Internet, har packats upp dem, verifierar dem och installerar dem i rätt katalog för språkspecifika för modulen.

Om du vill använda de uppdaterade hjälpfilerna skriver `Get-Help`. Du behöver inte starta om Windows eller Windows PowerShell. Om du vill uppdatera hjälp för moduler i katalogen $pshome, starta Windows PowerShell med alternativet ”Kör som administratör”.

Stöd för användare som inte har tillgång till Internet och användare bakom brandväggar, den nya [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet hämtar hjälpfiler till en katalog i filsystemet, till exempel en filresurs. Användarna kan sedan använda den [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) för att hämta uppdaterade hjälpfiler från filresursen.

Du kan använda den [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet för att uppdatera hjälp filer för alla eller specifika moduler i alla stöds UI kulturer. Du kan även ange en [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) i Windows PowerShell-profil. Som standard hämtar Windows PowerShell hjälpfilerna för en modul mer än en gång om dagen.

Moduler för Windows 8 och Windows Server 2012 ingår inte hjälpfiler. Om du vill hämta de senaste hjälpfilerna skriver `Update-Help`. Mer information skriver `Get-Help` (utan parametrar) eller se [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Om hjälpfilerna för en cmdlet inte är installerad på datorn, den [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet visar nu automatiskt genererade hjälp. Autogenererade-hjälpen innehåller kommandosyntax och instruktioner för att använda den [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) för att hämta hjälpfilerna.

En modul skapad kan stödja uppdateringsbar hjälp för sina modulen. Du kan inkludera hjälpfiler i modulen och använda uppdateringsbar hjälp för att uppdatera dem eller utelämna hjälpfilerna och använda uppdateringsbar hjälp för att installera dem. Läs mer om att stödja uppdateringsbar hjälp [stödja uppdateringsbar hjälp](http://go.microsoft.com/FWLink/?LinkID=242129) i MSDN.

### <a name="enhanced-online-help"></a>Förbättrad direkthjälp
Direkthjälpen för Windows PowerShell är en viktig resurs för alla användare, men det är särskilt viktigt för användare som inte eller går inte att installera uppdaterade hjälpfiler.

För att få hjälp online för Windows PowerShell-cmdleten, skriver du:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell öppnar onlineversionen av hjälpavsnittet i din standardwebbläsare.

Den **Get-Help-Online** funktion i Windows PowerShell 3.0 är nu ännu mer kraftfulla eftersom den fungerar även när hjälpfilerna för cmdleten inte har installerats på datorn. Den **Get-Help-Online** funktionen hämtar URI för onlinehjälpavsnittet från HelpUri-egenskapen för cmdletar och avancerade funktioner.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

Från och med Windows PowerShell 3.0, författare av C#-cmdlets kan fylla i **HelpUri** egenskapen genom att skapa en **HelpUri** attribut i cmdlet-klassen. Författare av avancerade funktioner kan definiera en **HelpUri** egenskapen på den **CmdletBinding** attribut. Värdet för den **HelpUri** egenskapen måste börja med ”http” eller ”https”.

Du kan även inkludera ett **HelpUri** värde i första relaterade länken till en XML-baserade cmdlet-hjälpfil eller. Länken direktiv av kommentarbaserad hjälp i en funktion.

Mer information om stöd för onlinehjälp finns [stödja onlinehjälp](http://go.microsoft.com/fwlink/?LinkId=242132) i MSDN.

### <a name="cim-integration"></a>CIM-integrering
Windows PowerShell 3.0 innehåller stöd för vanliga Information Model (CIM), som ger gemensamma definitioner av hanteringsinformation för system, nätverk, program och tjänster, så att de utbyte av hanteringsinformation mellan heterogena system. Stöd för CIM i Windows PowerShell 3.0, inklusive möjligheten att skapa Windows PowerShell-cmdlets baserat på nytt eller befintligt CIM-klasser, kommandon utifrån cmdlet definition XML-filer, stöd för CIM .NET Framework. API: et, CIM cmdlet: ar och 2.0 WMI-providers.

### <a name="session-configuration-files"></a>Konfigurationsfiler för session
Från och med Windows PowerShell 3.0 kan utforma du en anpassad sessionskonfiguration med hjälp av en fil. Konfigurationsfilen ny session kan du bestämma sessioner som använder sessionskonfigurationen, inklusive vilka moduler, skript, miljö och format-filer läses in i sessioner, vilka cmdlets och språk element-användare kan använda vilka moduler och skript som de kan köras och vilka variabler som de kan se.

Du kan utforma en session där användare kan endast köra cmdlets från en viss modul eller en session där användarna har fullständig språk, åtkomst till alla moduler och åtkomst till skript som utför avancerade åtgärder.

Kontrollen på den här nivån var endast tillgängligt för personer kan skriva ett C#-program eller ett skript för komplexa Start i tidigare versioner av Windows PowerShell. Nu kan kan alla medlemmar i gruppen Administratörer på datorn Anpassa en sessionskonfiguration med hjälp av en konfigurationsfil.

Använd för att skapa en konfigurationsfil för sessionen på [ny PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. Genomför session konfigurationsfilen till en sessionskonfiguration med hjälp av [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) eller [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.

Mer information finns i [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8) och [ny PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Schemalagda jobb och uppgiften Scheduler-integrering
Du kan nu schemalägga bakgrundsjobb för Windows PowerShell och hantera dem i Windows PowerShell och i Schemaläggaren.

Windows PowerShell schemalagda jobb är en användbar hybrid av Windows PowerShell-bakgrundsjobb och aktiviteter i Schemaläggaren.

Precis som Windows PowerShell bakgrundsjobb schemalagda jobb körs asynkront i bakgrunden. Instanser av schemalagda jobb som har slutförts kan hanteras med hjälp av jobb-cmdlets som [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442) och [Get-Job](https://technet.microsoft.com/en-us/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Du kan köra schemalagda jobb på en gång eller återkommande schema eller som svar på en åtgärd eller händelse som aktiviteter i Schemaläggaren. Du kan visa och hantera schemalagda jobb i Schemaläggaren, aktivera och inaktivera dem efter behov, köra dem eller använda dem som en mall och ange villkor under vilka jobb ska starta.

Dessutom kommer schemalagda jobb med en anpassad uppsättning cmdletar för att hantera dem. Cmdlets kan du skapa, redigera, hantera, inaktivera, och återaktivera schemalagda jobb, skapa schemalagda jobbet utlösare och ange alternativ för schemalagt jobb.

Mer information om schemalagda jobb finns [about_Scheduled_Jobs](https://technet.microsoft.com/en-us/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Förbättringar i Windows PowerShell-språk
Windows PowerShell 3.0 innehåller många funktioner som gör att dess språk enklare och enklare att använda och för att undvika vanliga fel. Förbättringarna innefattar egenskapen uppräkning, antal och längd egenskaper för skalära objekt, nya operatorer för omdirigering, omfångsändraren $Using, PSItem automatisk variabel, flexibla skript formatering, attribut för variabler, förenklad attribut argument, numeriska kommandonamn, parsning av stoppa operator, förbättrad matris splatting, nya bitars operatorer, ordnad ordlistor, PSCustomObject omvandling och förbättrad kommentarbaserad hjälp.

### <a name="new-core-cmdlets"></a>Ny-Kärncmdletar
Nya cmdletar har lagts till i Windows PowerShell Core-installationen, inklusive cmdletar för att hantera schemalagda jobb frånkopplade sessioner, CIM-integrering och uppdateras hjälpsystemet.

|||
|-|-|
|Lägg till JobTrigger|Ny JobTrigger|
|Connect-PSSession|Ny PSSessionConfigurationFile|
|ConvertFrom Json|New-PSTransportOption|
|ConvertTo Json|Ny PSWorkflowExecutionOption|
|Inaktivera JobTrigger|Ny PSWorkflowSession|
|Inaktivera-ScheduledJob|Ny ScheduledJobOption|
|Koppla från PSSession|Ny WinEvent|
|Aktivera JobTrigger|Ta emot PSSession|
|Aktivera-ScheduledJob|Registrera CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Ta bort CimInstance|
|Get-CimInstance|Ta bort-CimSession|
|Get-CimSession|Ta bort TypeData|
|Get-ControlPanelItem|Byt namn på datorn|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Ange CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Importera IseSnippet|Ange ScheduledJobOption|
|Anropa AsWorkflow|Visa kommando|
|Anropa CimMethod|Visa ControlPanelItem|
|Anropa RestMethod|Pausa jobb|
|Anropa WebRequest|Testa PSSessionConfigurationFile|
|Ny CimInstance|Avblockera-fil|
|Ny CimSession|Unregister-ScheduledJob|
|Ny CimSessionOption|Update-Help|
|Ny IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Förbättringar av befintliga Core-Cmdlets och leverantörer
Windows PowerShell 3.0 innehåller nya funktioner för befintliga cmdlets med förenklad syntax och nya parametrar för följande cmdlets: datorn cmdlets, CSV-cmdlet: ar, Get-ChildItem Get-Command-, Get-innehåll, Get-historik, måttobjekt-säkerhet cmdlet: ar, Select-Object, Välj sträng, dela sökväg, startprocessen, Tee-objektet, Test-Connection Lägg till medlem och WMI-cmdletar.

Windows PowerShell-providers har också förbättrats avsevärt, inklusive stöd för providern för att hantera Secure Socket Layer (SSL)-certifikat för Internet, stöd för autentiseringsuppgifter, beständiga nätverksenheter och alternativa dataströmmar i filsystem enheter.

### <a name="remote-module-import-and-discovery"></a>Remote modulimporten och identifiering
Windows PowerShell 3.0 utökar modulen identifiering, importerar och implicit fjärrkommunikation funktioner på fjärrdatorer. Modul-cmdlet: ar hämta moduler på fjärrdatorer och importerar modulerna till fjärrdatorer eller lokala datorn med hjälp av Windows PowerShell-fjärrkommunikation. Nytt stöd för CIM-session kan du använda CIM och WMI för att hantera Windows-datorer genom att importera kommandon till den lokala datorn som kör implicit på fjärrdatorn.

Mer information finns i hjälpavsnitten för den [Get-Module](https://technet.microsoft.com/en-us/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) och [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="enhanced-tab-completion"></a>Förbättrad Flikavslutande
Flikavslutande i Windows PowerShell-konsolen nu Slutför namnen på cmdlets, parametrar, parametervärden, uppräkningar, .NET Frameworks typer, COM-objekt, dolda kataloger och mer. Funktionen fliken slutförande skrivs om helt baserat på en ny parsern och abstract syntax trädet att stödja flera scenarier, inklusive InMemory-tolkning träd och mittlinjen flikavslutande.

### <a name="module-auto-loading"></a>Modulen automatisk inläsning
Den [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) nu hämtar alla cmdletar och funktioner från alla moduler som är installerade på datorn, även om modulen inte importeras till den aktuella sessionen.

När du får den cmdlet som du behöver använda du det direkt utan att importera alla moduler. Windows PowerShell-moduler är nu importeras automatiskt när du använder en cmdlet i modulen. Du behöver inte längre att söka efter modulen och importera det till att använda dess cmdletar.

Automatisk import av moduler utlöses med hjälp av cmdleten i ett kommando körs **Get-Command** för en cmdlet utan jokertecken eller körs [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) för en cmdlet utan jokertecken.

Du kan aktivera, inaktivera och konfigurera automatisk import av moduler med hjälp av den **$PSModuleAutoLoadingPreference** inställningsvariabeln.

Mer information finns i [about_Modules [v4]](https://technet.microsoft.com/en-us/library/94f57429-a539-4aee-bb0d-205cd7e801f9), [about_Preference_Variables [v4]](https://technet.microsoft.com/en-us/library/31344314-be29-4286-b039-afa5460cbe8b), och hjälpavsnitt för de [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) och [Import-Module ](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="module-experience-improvements"></a>Modulen upplevelse förbättringar
Windows PowerShell 3.0 ger avancerade funktioner som stöds för moduler, inklusive följande nya funktioner.

1. Modulen loggning för enskilda moduler (LogPipelineExecutionDetails) och nya ”aktivera på modulen loggning” grupprincipinställningen

2. Utökad Modulobjekt som exponerar värden från modulmanifestet

3. Nya **ExportedCommands** -egenskapen för moduler, inklusive kapslade moduler som kombinerar kommandon av alla typer av

4. Förbättrad identifieringen av tillgängliga (icke importerade) moduler, inklusive så att den **sökväg** och **ListAvailable** parametrar i samma kommando

5. Nya **DefaultCommandPrefix** nyckel i modulmanifest som undviker namnkonflikter utan att ändra koden i modulen.

6. Förbättrad modulen krav, inklusive fullständiga moduler som krävs i version och GUID och automatisk import av moduler som krävs

7. Tystare, effektiv drift av den [ny ModuleManifest](https://technet.microsoft.com/en-us/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.

8. Nya **modulen** parameter för #Requires

9. Förbättrad [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) med både **MinimumVersion** och **RequiredVersion** parametrar.

### <a name="simplified-command-discovery"></a>Förenklad kommandot identifiering
Du behöver inte längre att importera alla moduler för att identifiera kommandona som är tillgängliga för din session. I Windows PowerShell 3.0 den [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet hämtar alla kommandon från alla installerade moduler. Och om du använder ett kommando som exporterar kommandot modul importeras automatiskt i sessionen.

Den nya [Visa kommandot](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet är utformad särskilt för nybörjare. Du kan söka efter kommandon i ett fönster. Du kan visa alla kommandon eller filtrera efter modul, importera en modul genom att klicka på en knapp, Använd textrutor och listrutor för att konstruera ett giltigt kommando och sedan kopiera eller kör kommandot utan att lämna fönstret.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Förbättrad loggning, diagnostik och stöd för principen
Windows PowerShell 3.0 förbättrar loggning och spårning stöd för kommandon och moduler med stöd för händelsespårning i Windows (ETW) loggar, en redigerbar **LogPipelineExecutionDetails** egenskapen moduler och ”aktivera på modulen Loggning ”grupp principinställningen. Nu kan du få parametervärden från logginformation genom att visa loggegenskaperna.

### <a name="formatting-and-output-improvements"></a>Formatering och förbättringar av utdata
Ny formatering och utdata förbättringar förbättra effektiviteten för alla användare av Windows PowerShell. Förbättringarna innefattar omdirigering av utdata för alla dataströmmar, en förbättrad uppdateringstyp cmdlet som lägger till typer dynamiskt utan Format.ps1xml filer, radbyte i utdata, standard formateringsegenskaper av anpassade objekt, den **PSCustomObject** typ, förbättrad formatering för WMI-objekt och heterogena objekt och stöd för identifiering av metoden överlagringar.

### <a name="enhanced-console-host-experience"></a>Förbättrad konsolen värden upplevelse
Windows PowerShell-konsolen värdprogrammet har nya funktioner i Windows PowerShell 3.0 inklusive enkeltrådade som standard. Det nya alternativet ”Kör med PowerShell” i Utforskaren kan du köra skript i en obegränsad session genom att högerklicka. Nya konsolen värden starta logiken startar Windows PowerShell snabbare och nya teckensnitt kan du anpassa bekant konsolen fönstret upplevelse.

Mer information finns i [about_Run_With_PowerShell](https://technet.microsoft.com/en-us/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Ny Cmdlet och vara värd för API: er
Nya Cmdlet-API och värd API innehåller offentliga avancerade syntax träd (AST) API: er och API: er för växling av pipeline, kapslad pipelines, runspace pooler flikavslutande, Windows RT, föråldrade cmdlet-attribut och FunctionInfo-objektets egenskaper Verb och substantiv.

### <a name="performance-improvements"></a>Prestandaförbättringar
Betydande prestandaförbättringar i Windows PowerShell komma från den nya parsern språket bygger på dynamisk Runtime språk (DLR) i .NET Framework 4., tillsammans med runtime skript kompilering, motorn tillförlitlighet förbättringar och ändringar i den algoritmen för den [Get-ChildItem](https://technet.microsoft.com/en-us/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) som förbättra systemets prestanda, särskilt när söker nätverket delar.

### <a name="runas-and-shared-host-support"></a>RunAs- och delad värdgrupp Support
Windows PowerShell 3.0 ingår stöd för RunAs-och delade värden.

Den *RunAs* -funktionen för Windows PowerShell-arbetsflöde låter användare av en sessionskonfiguration skapa sessioner som körs med behörigheten för delade användarkontot. Detta gör att mindre privilegierade användare kan köra kommandon och skript med administratörsbehörighet och minskar behovet av att lägga till mindre erfarna användare i gruppen Administratörer.

Den **SharedHost** funktionen kan flera användare på flera datorer att ansluta till en Arbetsflödessession samtidigt och övervaka förloppet för ett arbetsflöde. Användare kan starta ett arbetsflöde på en dator och ansluter till sessionskonfigurationen för arbetsflödet på en annan dator utan att koppla från sessionen från den ursprungliga datorn. Användarna måste ha samma behörigheter och använda samma sessionskonfiguration. Mer information finns i ”kör ett Windows PowerShell-arbetsflöde” i komma igång med Windows PowerShell-arbetsflöde.

### <a name="special-character-handling-improvements"></a>Förbättringar för hantering av specialtecken
Att förbättra möjligheten för Windows PowerShell 3.0 att tolka och hanterar specialtecken felaktigt, den **LiteralPath** som hanterar specialtecken i sökvägar är giltig för nästan alla cmdlets som har en  **Sökvägen** parameter, inklusive den nya [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) och [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlets. Parsern innehåller också speciell logik för att förbättra hanteringen av backtick tecken (\`) och hakparenteser i filnamn och sökvägar.

## <a name="see-also"></a>Se även
- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)

