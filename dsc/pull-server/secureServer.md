---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Metodtips för hämtningsservern
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057713"
---
# <a name="pull-server-best-practices"></a>Metodtips för hämtningsservern

Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Sammanfattning: Det här dokumentet är avsett att inkludera processen och utökningsbarhet för att hjälpa teknikerna som förbereder för lösningen. Information bör ge bästa praxis som identifieras av kunder och sedan godkänt produktteam för att kontrollera rekommendationer är framtida riktar sig mot och anses vara stabil.

| |Doc-Info|
|:---|:---|
Författare | Michael Greene
Granskare | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Publicerad | April 2015

## <a name="abstract"></a>Abstrakt

Det här dokumentet är avsett att ge officiella vägledning för alla som planerar för en Windows PowerShell Desired State Configuration pull-serverimplementering. En pull-server är en enkel tjänst som ska vidtas på bara några minuter att distribuera. Även om det här dokumentet kommer att erbjuda teknisk vägledning som kan användas i en distribution, är värdet för det här dokumentet som referens för bästa praxis och vad du ska tänka på innan du distribuerar.
Läsare bör ha grundläggande kunskaper om DSC och de termer som används för att beskriva komponenterna som ingår i en DSC-distribution. Mer information finns i den [Windows PowerShell Desired State Configuration-översikt](/powershell/dsc/overview) avsnittet.
Eftersom DSC förväntas utvecklas på molnkadens kan förväntas också den underliggande tekniken inklusive hämtningsservern att utvecklas och ger nya möjligheter. Det här dokumentet innehåller en versionstabell i tillägget som innehåller referenser till tidigare versioner och referenser till framtida söker lösningar för att uppmuntra framtida Designer.

De två viktigaste avsnitten i det här dokumentet:

- Planera konfiguration
- Installationsguide

### <a name="versions-of-the-windows-management-framework"></a>Versioner av Windows Management Framework

Informationen i det här dokumentet är avsedd att gäller för Windows Management Framework 5.0. WMF 5.0 inte krävs för distribution och drift av en pull-server, är version 5.0 fokus för det här dokumentet.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

Desired State Configuration (DSC) är en plattform som möjliggör distribution och hantering konfigurationsdata genom att använda en bransch syntax med namnet Managed Object Format (MOF) för att beskriva Common Information Model (CIM). Det finns ett projekt med öppen källkod, Open Management Infrastructure (OMI), för att ytterligare utvecklingen av dessa standarder för olika plattformar, inklusive Linux och operativsystem för maskinvara. Mer information finns i den [DMTF sida länkar till MOF-specifikationer](https://www.dmtf.org/standards/cim), och [OMI dokument och källan](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell tillhandahåller en uppsättning språktillägg för Desired State Configuration som du kan använda för att skapa och hantera deklarativa konfigurationer.

### <a name="pull-server-role"></a>Pull-serverrollen

En pull-server är en centraliserad tjänst för att lagra konfigurationer som kommer att vara tillgänglig för målnoder.

Pull-serverrollen kan distribueras som en Web Server-instans eller en SMB-filresurs. Funktionen web server innehåller ett OData-gränssnitt och att inkludera välja funktioner för målnoder att rapportera tillbaka en bekräftelse av lyckats eller misslyckats eftersom konfigurationer tillämpas. Den här funktionen är användbar i miljöer där det finns ett stort antal målnoder.
När du har konfigurerat en målnod (kallas även en klient) för att peka på hämtningsservern den senaste konfigurationen data och eventuella nödvändiga skript hämtas och tillämpas. Detta kan inträffa som en enstaka distribution eller som ett nytt förekommer jobb som den gör också hämtningsservern en viktig tillgång för att hantera ändring i stor skala. Mer information finns i [Windows PowerShell Desired State Configuration hämta servrar](/powershell/dsc/pullServer) och

[Skicka och hämta Configuration lägen](/powershell/dsc/pullServer).

## <a name="configuration-planning"></a>Planera konfiguration

För alla programvara för företagsdistribution finns information som samlas in i förväg för att planera för rätt arkitektur och förberedas för de steg som krävs för att slutföra distributionen. Följande avsnitt innehåller information om hur du förbereder och organisationens anslutningarna som sannolikt måste ske i förväg.

### <a name="software-requirements"></a>Programvarukrav

Distributionen av en pull-servern kräver funktionen DSC-tjänsten i Windows Server. Den här funktionen introducerades i Windows Server 2012 och har uppdaterats via pågående versioner av Windows Management Framework (WMF).

### <a name="software-downloads"></a>Nedladdning av programvara

Förutom att installera det senaste innehållet från Windows Update, det finns två nedladdningar som anses vara bästa praxis att distribuera en DSC-hämtningsserver: Den senaste versionen av Windows Management Framework och en DSC-modul för att automatisera etableringen av pull-servern.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 innehåller en funktion för DSC-tjänsten. Funktionen för DSC-tjänsten tillhandahåller pull server-funktionalitet, inklusive binärfiler som har stöd för OData-slutpunkten.
WMF ingår i Windows Server och uppdateras på en snabb takt mellan Windows Server-versioner. [Nya versioner av WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) kan innehålla uppdateringar till funktionen DSC-tjänsten. Därför är det en bra idé att hämta den senaste versionen av WMF och granska viktig information för att avgöra om versionen innehåller en uppdatering av funktionen för DSC-tjänsten. Du bör även se avsnittet i viktig information som anger om den design för en uppdatering eller scenario statusen stabil eller experimentella.
Om du vill tillåta för en smidig övergång cykel enskilda funktioner kan deklareras stabil, är vilket anger att funktionen redo att användas i en produktionsmiljö, även om WMF släpps i en förhandsversion.
Andra funktioner som tidigare har uppdaterats av WMF versioner (se WMF viktig information för detaljerat):

- Windows PowerShell Windows PowerShell Integrated Scripting
- Environment (ISE) Windows PowerShell-webbtjänster (Management OData
- IIS-tillägget) Windows PowerShell Desired State Configuration (DSC)
- Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC-resurs

En pull-serverdistribution kan förenklas genom att etablera tjänsten med hjälp av ett DSC-konfigurationsskript. Det här dokumentet innehåller konfigurationsskript som kan användas för att distribuera en klar servernoden i produktion. Om du vill använda konfigurationsskript, en DSC-modul krävs det vill säga inte ingår i Windows Server. Nödvändiga Modulnamn **xPSDesiredStateConfiguration**, som innehåller DSC-resurs **xDscWebService**. Modulen xPSDesiredStateConfiguration kan laddas ned [här](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Använd den `Install-Module` cmdlet från den **PowerShellGet** modulen.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Den **PowerShellGet** modulen hämtar modulen till:

`C:\Program Files\Windows PowerShell\Modules`

Planera uppgift|
---|
Du har åtkomst till installationsfilerna för Windows Server 2012 R2?|
Distributionsmiljö har Internetåtkomst för att hämta WMF och modulen från galleriet online?|
Hur ska du installera de senaste säkerhetsuppdateringarna när du har installerat operativsystemet?|
Miljön har Internetåtkomst för att hämta uppdateringar eller den har en lokal Windows Server Update Services (WSUS)-server?|
Har du åtkomst till installationsfilerna för Windows Server som redan omfattar uppdateringar via offline inmatning?|

### <a name="hardware-requirements"></a>Maskinvarukrav

Hämta distributioner stöds på både fysiska och virtuella servrar. Storlekskraven för hämtningsservern överensstämmer med kraven för Windows Server 2012 R2.

CPU: 1,4 GHz 64-bitars processor minne: 512 MB ledigt diskutrymme: 32 GB nätverk: Gigabit Ethernet-kort

Planera uppgift|
---|
Vill du distribuera på fysisk maskinvara eller på en virtualiseringsplattform?|
Vad är processen för att begära en ny server för målmiljön?|
Vad är den genomsnittliga arbetet tiden för en server ska bli tillgänglig?|
Vilken storlek ska du serverbegäran?|

### <a name="accounts"></a>Konton

Det finns inga krav på tjänstkonto att distribuera en pull-serverinstans.
Det finns dock scenarier där webbplatsen kan köras i kontexten för ett lokalt användarkonto.
Till exempel om det finns ett behov av att åtkomst en storage-resurs för webbplatsens innehåll och Windows Server eller enhet som är värd för storage-resurs är inte ansluten till en domän.

### <a name="dns-records"></a>DNS-poster

Du behöver ett servernamn som du använder när du konfigurerar klienter för att arbeta med en pull-servermiljö.
I testmiljöer, oftast av serverns värdnamn eller IP-adressen för servern kan användas om DNS-namnmatchningen inte är tillgänglig.
I produktionsmiljöer eller i en laboratoriemiljö som är avsedd att representera en Produktionsdistribution, är det bästa sättet att skapa en DNS CNAME-post.

Ett DNS CNAME kan du skapa ett alias för att referera till din värd (A) post.
Syftet med den ytterligare namnposten är att öka flexibiliteten bör en ändring krävas i framtiden.
En CNAME-post kan hjälpa dig för att isolera klientkonfigurationen så att ändringar i servermiljö, t.ex ersätter en pull-server eller lägga till ytterligare pull-servrar, inte kräver en motsvarande ändring i klientkonfigurationen.

Tänk lösningsarkitekturen när du väljer ett namn för DNS-posten.
Om med hjälp av belastningsutjämning, måste certifikatet som används för att skydda trafik via HTTPS kan dela samma namn som DNS-posten.

Scenario |Bästa praxis
:---|:---
Testmiljö |Återskapa planerad produktionsmiljön, om möjligt. Ett värdnamn för servern är lämpligt för enkel konfigurationer. Om DNS inte är tillgänglig, kan en IP-adress användas i stället för ett värdnamn.|
Ennodsdistribution |Skapa en DNS CNAME-post som pekar på serverns värdnamn.|

Mer information finns i [konfigurerar DNS för resursallokering i Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Planera uppgift|
---|
Vet du att kontakta om du vill att DNS-poster som skapats och ändrats?|
Vad är den genomsnittliga arbetet för en begäran om en DNS-post?|
Behöver du begär statiska värdnamn (A)-poster för servrar?|
Vad kommer du begär som en CNAME-post?|
Om det behövs, vilken typ av belastningsutjämning lösningen ska du använda? (se avsnittet Utjämning av nätverksbelastning för information)|

### <a name="public-key-infrastructure"></a>Infrastruktur för offentliga nycklar

De flesta organisationer kräver i dag att nätverkstrafik, särskilt trafik som innehåller sådana känsliga data hur servrar har konfigurerats, måste verifieras och krypterad under överföringen.
Det är möjligt att distribuera en pull-server som använder HTTP som underlättar kundernas begäranden i klartext, är det en bra idé att säker trafik med hjälp av HTTPS. Tjänsten kan konfigureras för att använda HTTPS med en uppsättning parametrar i DSC-resursen i **xPSDesiredStateConfiguration**.

Certifikatkrav för säker HTTPS-trafik för hämtningsservern skiljer inte skydda någon annan webbplats för HTTPS. Den **webbservern** mall i Windows Server-certifikat Services uppfyller de nödvändiga funktionerna.

Planera uppgift|
---|
Om certifikatförfrågningar inte sker automatiskt, som du behöver du kontakta begäranden ett certifikat?|
Vad är den genomsnittliga tid för begäran?|
Hur kommer certifikatfilen överföras till dig?|
Hur kommer certifikatets privata nyckel överföras till dig?|
Hur lång är förfallotiden som standard?|
Har du reglerats på ett DNS-namn för pull-servermiljö, som du kan använda för certifikatets namn?|

### <a name="choosing-an-architecture"></a>Välja en arkitektur

En pull-server kan distribueras med hjälp av antingen en webbtjänst som finns på IIS eller en SMB-filresurs. I de flesta fall är ger web service-alternativet större flexibilitet. Det är inte ovanligt att HTTPS-trafik som passerar nätverksgränserna, medan SMB-trafik ofta filtreras eller blockeras mellan nätverk. Webbtjänsten finns också möjlighet att inkludera en Efterlevnadsstatus Server eller Web Reporting Manager (båda avsnitten kommer att åtgärdas i en framtida version av det här dokumentet) som tillhandahåller en mekanism för klienter att rapportera status tillbaka till en server för central synlighet.
SMB tillhandahåller ett alternativ för miljöer där nolltoleransprincip en webbserver inte bör användas och för andra miljökrav som gör en rollen som webbserver oönskade.
Kom ihåg att utvärdera kraven för signering och kryptering av trafik i båda fallen. HTTPS och SMB-signering för IPSEC-principer är alla alternativ värt överväger.

#### <a name="load-balancing"></a>Belastningsutjämning

Klienter som interagerar med webbtjänsten gör en begäran om information som returneras i ett enda svar. Inga sekventiella förfrågningar krävs, så det inte är nödvändigt för belastningsutjämning för plattformen för att säkerställa sessioner bibehålls på en enskild server när som helst i tid.

Planera uppgift|
---|
Vilken lösning ska användas för belastningsutjämning trafik mellan servrar?|
Om du använder en maskinvarubaserad belastningsutjämnare som tar en begäran om att lägga till en ny konfiguration för enheten?|
Vad är den genomsnittliga arbetet för en begäran om att konfigurera en ny load balanced webbtjänsten?|
Vilken information måste utföras för begäran?|
Behöver du en ytterligare IP-adress eller teamet som ansvarar för Utjämning av nätverksbelastning hanterar som?|
Har du DNS-poster som behövs, och detta måste av teamet som ansvarar för att konfigurera lösningen för belastningsutjämning?|
Belastningsutjämningslösning kräver att PKI ska hanteras av enheten eller kan den belastningsutjämna HTTPS-trafik så länge det finns inga sessionskrav?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Mellanlagring konfigurationer och moduler på hämtningsservern

Som en del av planeringen av konfigurationen, behöver du tycker om vilka DSC-moduler och konfigurationer kommer att finnas av pull-servern. I syfte att planera konfigurationen är det viktigt att du har grundläggande kunskaper om hur du förbereder och distribuerar innehåll till en pull-server.

Det här avsnittet kommer i framtiden, expandera och ingår i en Funktionsguide för DSC-Hämtningsserver.  Guiden kommer att diskutera dagliga processen för att hantera moduler och konfigurationer över tid med automation.

#### <a name="dsc-modules"></a>DSC-moduler

Klienter som begär en konfiguration måste de DSC-modulerna som krävs. En funktion för pull-servern är att automatisera distribution på begäran av DSC-moduler till klienter. Om du distribuerar en pull-server för första gången, kanske som ett labb eller ett konceptbevis kan ska du förmodligen är beroende av DSC-moduler som är tillgängliga från offentliga databaser, till exempel PowerShell-galleriet eller PowerShell.org GitHub-lagringsplatser för DSC-moduler .

Det är viktigt att komma ihåg att även för betrodda online källor, till exempel PowerShell-galleriet, alla moduler som hämtas från en offentlig databasen bör granskas av någon med PowerShell erfarenhet och kunskap om miljön där modulerna som kommer att använda före som används i produktion. Det är ett bra tillfälle att söka efter eventuella ytterligare nyttolast i den modul som kan tas bort, till exempel dokumentation och skript för att slutföra den här uppgiften. Detta minskar nätverkets bandbredd per klient i sin första begäran när moduler ska laddas ned över nätverket från servern till klienten.

Varje modul måste paketeras i ett visst format, en ZIP-fil med namnet ModuleName_Version.zip som innehåller modulen nyttolasten. När filen har kopierats till servern måste du skapa en fil för kontrollsumma. När klienter ansluter till servern, används kontrollsumman för att kontrollera innehållet i DSC-modul inte har ändrats sedan den publicerades.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Planera uppgift|
---|
Om du planerar en test- eller labb-miljö är vilka scenarier för att verifiera?|
Det är allmänt tillgängliga moduler som innehåller resurser så att den täcker allt du behöver eller behöver du skapa dina egna resurser?|
Din miljö har Internetåtkomst för att hämta offentliga moduler?|
Vem är ansvarig för att granska DSC moduler?|
Om du planerar en produktionsmiljö vad ska du använda som en lokal databas för lagring av DSC-moduler?|
Accepterar ett centralt team DSC-moduler från programteam? Vad blir processen?|
Du automatiserar paketering, kopiera och skapa en kontrollsumma för produktionsklara DSC-moduler till servern, från din lagringsplats för källa?|
Blir ditt team ansvarar för att hantera plattformen automation?|

#### <a name="dsc-configurations"></a>DSC-konfigurationer

Syftet med en pull-server är att tillhandahålla en centraliserad mekanism för att distribuera DSC-konfigurationer till klientnoder. Konfigurationerna som lagras på servern som MOF-dokument.
Varje dokument kommer att namnges med ett unikt **Guid**. När klienterna är konfigurerade för att ansluta till en pull-server, de också tilldelas den **Guid** för hur de ska begära. Det här systemet för att referera till konfigurationer av **Guid** garanterar globala unikhet och är flexibel, så att en konfiguration kan användas med precisionen per nod eller som en rollkonfiguration som sträcker sig över flera servrar som ska ha identiska konfigurationer.

#### <a name="guids"></a>GUID

Planera för konfiguration av **GUID** är värt att ytterligare uppmärksamhet när du funderar på en pull-serverdistribution. Det finns inga specifika krav för hur du hanterar **GUID** och processen kan förväntas vara unikt för varje miljö. Processen kan variera mellan enkla eller komplexa: en centralt lagrade CSV-fil, en enkel SQLtabell, en CMDB eller en komplex lösningar som kräver integrering med en annan lösning för verktyget eller programvara. Det finns två sätt:

- **Tilldela GUID per server** – ger ett mått på assurance att varje serverkonfiguration styrs individuellt. Detta ger en nivå av precision runt uppdateringar och fungerar bra i miljöer med några servrar.
- **Tilldela GUID per serverrollen** – alla servrar som utför samma funktion, till exempel webbservrar, Använd samma GUID för att referensdata konfiguration som krävs.  Tänk på att om många servrar delar samma GUID kan alla skulle uppdateras samtidigt när konfigurationen ändras.

  GUID-värdet är något som bör övervägas känsliga data eftersom den kan användas av någon med skadliga avsikter att få information om hur servrar distribueras och konfigurerad i din miljö. Mer information finns i [på ett säkert sätt tilldela GUID i PowerShell Desired State Configuration Pull-läge](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Planera uppgift|
---|
Vem är ansvarig för att kopiera konfigurationer i i pull-servermappen när de är klara?|
Om konfigurationer som skapats av en program-team, vad kommer processen att du lämnar dem?|
Ska du använda en lagringsplats för att lagra konfigurationer som de som skapats, i team?|
Kommer du att automatisera processen med att kopiera konfigurationer till servern och skapa en kontrollsumma när de är klara?|
Hur ska du mappa GUID till servrar eller roller och där det sparas?|
Det kommer du att använda som en process för att konfigurera klientdatorer och hur det integreras med din process för att skapa och lagra konfiguration GUID?|

## <a name="installation-guide"></a>Installationsguide

*Skript som anges i det här dokumentet är stabil exempel. Läs alltid igenom skript noggrant innan du kör dem i en produktionsmiljö.*

### <a name="prerequisites"></a>Förutsättningar

Använd följande kommando för att kontrollera PowerShell-versionen på din server.

```powershell
$PSVersionTable.PSVersion
```

Om det är möjligt, uppgradera till den senaste versionen av Windows Management Framework.
Därefter, hämtar du den `xPsDesiredStateConfiguration` modul med följande kommando.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Kommandot begär ditt godkännande innan du laddar ned modulen.

### <a name="installation-and-configuration-scripts"></a>Skript för installation och konfiguration

Den bästa metoden för att distribuera en DSC-hämtningsserver är att använda en DSC-konfigurationsskript. Det här dokumentet kommer att presentera skript, inklusive både grundläggande inställningar som konfigurerar bara DSC-webbtjänsten och avancerade inställningar som konfigurerar en Windows Server slutpunkt till slutpunkt inklusive DSC webbtjänst.

Anm  För närvarande den `xPSDesiredStateConfiguration` DSC-modulen kräver att servern ska vara EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Grundläggande konfiguration för Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Avancerad konfiguration för Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Kontrollera pull-serverfunktioner

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Konfigurera klienter

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Ytterligare referenser, kodfragment och exempel

Det här exemplet visar hur du manuellt initiera en klientanslutning (kräver WMF5) för testning.

```powershell
Update-DscConfiguration –Wait -Verbose
```

Den [Lägg till DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet används för att lägga till en typ CNAME-post till en DNS-zon.

PowerShell-funktionen för att [skapar en kontrollsumma och publicera DSC MOF till SMB-Pullserver](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genererar automatiskt krävs kontrollsumma och kopierar sedan både MOF konfigurations- och kontrollsumma filer till SMB-pullserver.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Tillägg – förstå ODATA-tjänstdata filtyper

En datafil lagras för att skapa information under distributionen av en pull-server som innehåller OData-webbtjänst. Typ av fil beror på operativsystemet, enligt beskrivningen nedan.

- **Windows Server 2012** filtypen kommer alltid att .mdb
- **Windows Server 2012 R2** filtypen som standard edb såvida inte en .mdb har angetts i konfigurationen

I den [avancerade exempelskript](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) för att installera en Pull-servern finns också ett exempel på hur du automatiskt styr inställningarna i web.config-filen för att förhindra alla risken för fel som orsakas av filtyp.
