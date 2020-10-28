---
ms.date: 06/12/2017
description: Det här dokumentet innehåller metod tips för att hjälpa tekniker som distribuerar DSC-pull-servern.
keywords: DSC, PowerShell, konfiguration, installation
title: Metodtips för hämtningsservern
ms.openlocfilehash: 0021baa219a0936405eccf2cc7741e042f8bf09f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664322"
---
# <a name="pull-server-best-practices"></a>Metodtips för hämtningsservern

Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Sammanfattning: det här dokumentet är avsett att omfatta process och utöknings barhet för att hjälpa tekniker som förbereder lösningen. Informationen bör ge bästa praxis som identifieras av kunder och sedan verifieras av produkt teamet för att säkerställa att rekommendationerna är stabila och anses stabila.

- Författare: Michael Greene
- Granskare: Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
- Publicerad: april 2015

## <a name="abstract"></a>Sammanfattning

Det här dokumentet är utformat för att ge den officiella vägledningen för alla som planerar för en Windows PowerShell Desired State Configuration-hämtning av hämtnings servrar. En pull-server är en enkel tjänst som bara tar några minuter att distribuera. Även om det här dokumentet kommer att erbjuda teknisk instruktions vägledning som kan användas i en distribution, är värdet för det här dokumentet som en referens för bästa praxis och vad du behöver tänka på innan du distribuerar. Läsarna bör ha grundläggande kunskaper om DSC och de termer som används för att beskriva de komponenter som ingår i en DSC-distribution. Mer information finns i avsnittet [Översikt över Desired State Configuration i Windows PowerShell](/powershell/scripting/dsc/overview/overview) . Eftersom DSC förväntas utvecklas på Cloud takt förväntas den underliggande tekniken, inklusive hämtnings servern, att utvecklas och introducera nya funktioner. Det här dokumentet innehåller en versions tabell i bilagan som innehåller referenser till tidigare versioner och referenser till kommande lösningar för att uppmuntra de vanliga designerna.

De två huvud avsnitten i det här dokumentet:

- Konfigurations planering
- Installationsguide

### <a name="versions-of-the-windows-management-framework"></a>Versioner av Windows Management Framework

Informationen i det här dokumentet är avsedd att användas för Windows Management Framework 5,0. Även om WMF 5,0 inte krävs för att distribuera och använda en hämtnings Server är version 5,0 fokus i det här dokumentet.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

Önskad tillstånds konfiguration (DSC) är en hanterings plattform som gör det möjligt att distribuera och hantera konfigurations data med hjälp av en bransch-syntax med namnet Managed Object Format (MOF) som beskriver Common Information Model (CIM). Ett projekt med öppen källkod, öppen hanterings infrastruktur (OMI), finns för att utveckla dessa standarder på olika plattformar, inklusive Linux-och nätverks maskin varu operativ system. Mer information finns i DMTF- [sidan länka till MOF-specifikationer](https://www.dmtf.org/standards/cim)och [OMI-dokument och-källa](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell innehåller en uppsättning språk tillägg för önskad tillstånds konfiguration som du kan använda för att skapa och hantera deklarativ konfigurationer.

### <a name="pull-server-role"></a>Hämta server roll

En pull-server tillhandahåller en centraliserad tjänst för att lagra konfigurationer som kommer att vara tillgängliga för mål noder.

Hämtnings Server rollen kan distribueras antingen som en webb Server instans eller en SMB-filresurs. Webb server funktionen innehåller ett OData-gränssnitt och kan även inkludera funktioner för målnoden för att rapportera om en bekräftelse eller ett haveri som har tillämpats. Den här funktionen är användbar i miljöer där det finns ett stort antal mål noder. När du har konfigurerat en målnod (kallas även en klient) för att peka på hämtnings servern, laddas de senaste konfigurations data och eventuella skript som krävs ned och tillämpas. Detta kan ske vid en enstaka distribution eller som ett jobb som körs på nytt, vilket även gör hämtnings servern till en viktig till gång för att hantera förändringar i skala. Mer information finns i [Windows PowerShell Desired State Configuration pull-servrar](pullserver.md) och [push och pull Configuration Modes](pullserver.md).

## <a name="configuration-planning"></a>Konfigurations planering

För distribution av företags program vara finns det information som kan samlas in i förväg för att planera för rätt arkitektur och förberedas för de steg som krävs för att slutföra distributionen. I följande avsnitt finns information om hur du förbereder och de organisatoriska anslutningar som sannolikt kommer att behöva inträffa i förväg.

### <a name="software-requirements"></a>Programvarukrav

För att kunna distribuera en pull-server krävs DSC-funktionen i Windows Server. Den här funktionen introducerades i Windows Server 2012 och har uppdaterats genom pågående versioner av Windows Management Framework (WMF).

### <a name="software-downloads"></a>Hämtning av program vara

Förutom att installera det senaste innehållet från Windows Update, finns det två hämtnings bara filer som anses vara bästa praxis för att distribuera en DSC-pull-server: den senaste versionen av Windows Management Framework och en DSC-modul för att automatisera hämtning av Server etablering.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 innehåller en funktion som kallas DSC-tjänsten. Funktionen DSC-tjänst tillhandahåller hämtnings Server funktioner, inklusive binärfiler som stöder OData-slutpunkten. WMF ingår i Windows Server och uppdateras på en smidig takt mellan Windows Server-versioner.
[Nya versioner av WMF 5,0](https://www.microsoft.com/download/details.aspx?id=54616) kan innehålla uppdateringar av DSC-tjänstens funktion. Av den anledningen är det bäst att ladda ned den senaste versionen av WMF och granska viktig information för att ta reda på om versionen innehåller en uppdatering av DSC-tjänstens funktion. Du bör också läsa avsnittet i viktig information som anger om design status för en uppdatering eller ett scenario visas som stabil eller experimentell. För att möjliggöra en smidig lanserings cykel kan enskilda funktioner deklareras som stabila, vilket innebär att funktionen är redo att användas i en produktions miljö även om WMF lanseras i för hands versionen. Andra funktioner som tidigare har uppdaterats av WMF-versioner (mer information finns i versions kommentarerna för WMF):

- Windows PowerShell Windows PowerShell-integrerat skript
- Environment (ISE) Windows PowerShell-webbtjänster (hantering OData
- IIS-tillägg) Windows PowerShell Desired State Configuration (DSC)
- Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC-resurs

En pull-Server-distribution kan för enklas genom att tillhandahålla tjänsten med hjälp av ett DSC-konfigurations skript. Det här dokumentet innehåller konfigurations skript som kan användas för att distribuera en produktions klar Server-nod. Om du vill använda konfigurations skripten krävs en DSC-modul som inte ingår i Windows Server. Namnet på den obligatoriska modulen är **xPSDesiredStateConfiguration** , som innehåller DSC- **xDscWebService** . XPSDesiredStateConfiguration-modulen kan hämtas [här](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Använd `Install-Module` cmdleten från **PowerShellGet** -modulen.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Modulen **PowerShellGet** hämtar modulen till:

`C:\Program Files\Windows PowerShell\Modules`

Planerings uppgift

- Har du åtkomst till installationsfilerna för Windows Server 2012 R2?
- Kommer distributions miljön att ha Internet åtkomst för att hämta WMF och modulen från Onlinegalleri?
- Hur installerar du de senaste säkerhets uppdateringarna efter att du har installerat operativ systemet?
- Kommer miljön att ha Internet åtkomst för att hämta uppdateringar eller kommer att ha en lokal Windows Server Update Services (WSUS)-Server?
- Har du åtkomst till Windows Server-installationsfiler som redan innehåller uppdateringar via offline-inmatning?

### <a name="hardware-requirements"></a>Maskinvarukrav

Hämtnings Server distributioner stöds på både fysiska och virtuella servrar. Storleks kraven för hämtnings servern överensstämmer med kraven för Windows Server 2012 R2.

- CPU: 1,4 GHz 64-bitars processor
- Minne: 512 MB
- Disk utrymme: 32 GB
- Nätverk: Gigabit Ethernet-kort

Planerings uppgift

- Kommer du att distribuera på en fysisk maskin vara eller en Virtualization-plattform?
- Vad är processen för att begära en ny server för mål miljön?
- Vilken är den genomsnittliga leverans tiden för en server att bli tillgänglig?
- Vilken storleks server kommer du att begära?

### <a name="accounts"></a>Konton

Det finns inga tjänst konto krav för att distribuera en pull-serverinstans. Det finns dock scenarier där webbplatsen kan köras i kontexten för ett lokalt användar konto. Om det till exempel finns behov av att komma åt en lagrings resurs för webbplats innehåll och antingen Windows-servern eller enheten som är värd för lagrings resursen inte är domänansluten.

### <a name="dns-records"></a>DNS-poster

Du behöver ett server namn som du kan använda när du konfigurerar klienter för att arbeta med en pull-server-miljö.
I test miljöer används vanligt vis serverns värdnamn, eller så kan IP-adressen för servern användas om DNS-namnmatchning inte är tillgänglig. I produktions miljöer eller i en labb miljö som är avsedd att representera en produktions distribution är det bästa sättet att skapa en DNS CNAME-post.

Med en DNS CNAME kan du skapa ett alias för att referera till värd posten (A). Avsikten med den extra namn posten är att öka flexibiliteten om en ändring krävs i framtiden. En CNAME kan hjälpa till att isolera klient konfigurationen så att ändringar i Server miljön, till exempel att ersätta en hämtnings Server eller lägga till ytterligare pull-servrar, kräver ingen motsvarande ändring i klient konfigurationen.

Behåll lösnings arkitekturen i åtanke när du väljer ett namn för DNS-posten. Om du använder belastnings utjämning måste certifikatet som används för att skydda trafik över HTTPS dela samma namn som DNS-posten.

|       Scenario        |                                                                                         Metodtips
|:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|Testmiljö       | Återskapa den planerade produktions miljön, om möjligt. Ett server namn är lämpligt för enkla konfigurationer. Om DNS inte är tillgängligt kan en IP-adress användas i stället för ett värdnamn.
|Distribution av en nod | Skapa en DNS CNAME-post som pekar på serverns värdnamn.

Mer information finns i [Konfigurera DNS Round Robin i Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Planerings uppgift

- Vet du vem du ska kontakta så att DNS-poster skapas och ändras?
- Vad är genomsnittet för en begäran om en DNS-post?
- Behöver du begära statiska värdnamn (A) för servrar?
- Vad kommer du att begära som CNAME?
- Om det behövs, vilken typ av belastnings Utjämnings lösning kommer du att använda? (se avsnittet med rubriken belastnings utjämning för mer information)

### <a name="public-key-infrastructure"></a>Infrastruktur för offentliga nycklar

De flesta organisationer i dag kräver att nätverks trafik, särskilt trafik som inkluderar sådana känsliga data som servrar konfigureras, måste verifieras och/eller krypteras under överföringen.
Även om det är möjligt att distribuera en pull-server med HTTP som underlättar klient begär anden i klartext, är det en bra idé att skydda trafiken med HTTPS. Tjänsten kan konfigureras att använda HTTPS med en uppsättning parametrar i DSC- **xPSDesiredStateConfiguration** .

Certifikat kraven för säker HTTPS-trafik för hämtnings servern skiljer sig inte från att skydda andra HTTPS-webbplatser. **Webb server** mal len i en Windows Server Certificate Services uppfyller de funktioner som krävs.

Planerings uppgift

- Om du inte automatiserar certifikat begär Anden måste du kontakta för att begära ett certifikat?
- Vilken är den genomsnittliga leveransen för begäran?
- Hur överförs certifikat filen till dig?
- Hur överförs certifikatets privata nyckel till dig?
- Hur länge är standard förfallo tiden?
- Har du kvittat dig på ett DNS-namn för pull Server-miljön, som du kan använda för certifikat namnet?

### <a name="choosing-an-architecture"></a>Välja en arkitektur

En hämtnings Server kan distribueras med antingen en webb tjänst som finns på IIS eller en SMB-filresurs. I de flesta fall ger alternativet för webb tjänsten större flexibilitet. Det är inte ovanligt att HTTPS-trafik passerar nätverks gränserna, medan SMB-trafik ofta filtreras eller blockeras mellan nätverk. Webb tjänsten erbjuder också alternativet att inkludera en inställnings Server eller Web repor ting Manager (båda ämnen som ska åtgärdas i en framtida version av det här dokumentet) som ger en mekanism för klienter att rapportera status tillbaka till en server för centraliserad synlighet. SMB innehåller ett alternativ för miljöer där en princip anger att en webb server inte ska användas och andra miljö krav som gör en webb server roll olämplig. I båda fallen måste du komma ihåg att utvärdera kraven för signering och kryptering av trafik. HTTPS-, SMB-signering och IPSEC-principer är alla alternativ som är värda att beakta.

#### <a name="load-balancing"></a>Belastningsutjämning

Klienter som interagerar med webb tjänsten gör en begäran om information som returneras i ett enda svar. Inga sekventiella begär Anden krävs, så det är inte nödvändigt för belastnings Utjämnings plattformen att säkerställa att sessioner upprätthålls på en enskild server vid varje tidpunkt.

Planerings uppgift

- Vilken lösning ska användas för belastnings Utjämnings trafik mellan servrar?
- Om du använder en maskinvarubaserad belastningsutjämnare, som tar en förfrågan om att lägga till en ny konfiguration till enheten?
- Vad är genomsnittet för en begäran om att konfigurera en ny belastningsutjämnad webb tjänst?
- Vilken information kommer att krävas för begäran?
- Behöver du begära ytterligare en IP-adress eller teamet som ansvarar för belastnings Utjämnings referensen?
- Har du de DNS-poster som behövs och kommer att krävas av teamet som ansvarar för att konfigurera belastnings Utjämnings lösningen?
- Kräver belastnings Utjämnings lösningen att PKI hanteras av enheten eller kan den belastningsutjämna HTTPS-trafik så länge det inte finns några krav för sessionen?

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Mellanlagring av konfigurationer och moduler på hämtnings servern

Som en del av konfigurations planeringen måste du tänka på vilka DSC-moduler och konfigurationer som ska hanteras av hämtnings servern. För konfigurations planering är det viktigt att du har en grundläggande förståelse för hur du förbereder och distribuerar innehåll till en pull-server.

I framtiden kommer det här avsnittet att expanderas och ingå i en funktions guide för DSC-pull-server. Guiden diskuterar dag till dags process för att hantera moduler och konfigurationer över tid med automatisering.

#### <a name="dsc-modules"></a>DSC-moduler

Klienter som begär en konfiguration kommer att behöva de DSC-moduler som krävs. En funktion i pull-servern är att automatisera distributionen på begäran av DSC-moduler till klienter. Om du distribuerar en pull-server för första gången, kanske som labb eller koncept bevis, kommer du troligen att vara beroende av DSC-moduler som är tillgängliga från offentliga databaser, till exempel PowerShell-galleriet eller PowerShell.org GitHub-lagringsplatsen för DSC-moduler.

Det är viktigt att komma ihåg att även för betrodda onlinekällor som PowerShell-galleriet, alla moduler som hämtas från ett offentligt lager bör granskas av någon med PowerShell-erfarenhet och kunskap om miljön där modulerna används innan de används i produktionen. När du slutför den här uppgiften är det en lämplig tid att söka efter ytterligare en nytto Last i modulen som kan tas bort, till exempel dokumentation och exempel skript. Detta minskar nätverks bandbredden per klient i den första begäran, när moduler ska laddas ned över nätverket från server till klient.

Varje modul måste paketeras i ett särskilt format, en ZIP-fil med namnet ModuleName_Version.zip som innehåller modulens nytto Last. När filen har kopierats till servern måste en kontroll Summa fil skapas.
När klienter ansluter till servern används kontroll summan för att kontrol lera att innehållet i DSC-modulen inte har ändrats sedan den publicerades.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Planerings uppgift

- Om du planerar en test-eller labb miljö vars scenarier är nyckel att verifiera?
- Finns det offentligt tillgängliga moduler som innehåller resurser för att omfatta allt du behöver eller behöver du redigera dina egna resurser?
- Kommer din miljö att ha Internet åtkomst för att hämta offentliga moduler?
- Vem kommer att ansvara för att granska DSC-moduler?
- Om du planerar en produktions miljö vad kommer du att använda som lokal lagrings plats för att lagra DSC-moduler?
- Accepterar Central team DSC-moduler från program team? Vad kommer processen att vara?
- Kommer du att automatisera paketering, kopiering och skapande av en kontroll summa för produktions klara DSC-moduler till servern från din lagrings platsen?
- Är ditt team ansvarigt för att hantera Automation-plattformen också?

#### <a name="dsc-configurations"></a>DSC-konfigurationer

Syftet med en pull-server är att tillhandahålla en central mekanism för att distribuera DSC-konfigurationer till klient-noder. Konfigurationerna lagras på servern som MOF-dokument. Varje dokument får ett unikt **GUID** -namn. När klienterna är konfigurerade för att ansluta till en pull-server får de också **GUID** för den konfiguration de bör begära. Det här systemet med referenser till konfigurationer efter **GUID** garanterar global unikhet och är flexibelt så att en konfiguration kan tillämpas med granularitet per nod, eller som en roll konfiguration som omfattar många servrar som ska ha identiska konfigurationer.

#### <a name="guids"></a>GUID

Planering av konfigurations- **GUID** är värda ytterligare uppmärksamhet vid användning av en pull-Server-distribution. Det finns inget särskilt krav för att hantera **GUID** och processen är förmodligen unik för varje miljö. Processen kan vara mellan enkla och komplexa: en centralt lagrad CSV-fil, en enkel SQL-tabell, en CMDB eller en komplex lösning som kräver integrering med ett annat verktyg eller en program varu lösning. Det finns två allmänna metoder:

- **Tilldelning av GUID per server** – ger ett mått på att varje server konfiguration kontrol leras individuellt. Detta ger en nivå av precision kring uppdateringar och kan fungera bra i miljöer med några få servrar.
- **Tilldela GUID per server roll** – alla servrar som utför samma funktion, till exempel webb servrar, använder samma GUID för att referera till nödvändiga konfigurations data. Tänk på att om många servrar delar samma GUID, så uppdateras alla samtidigt när konfigurationen ändras.

  GUID är något som ska betraktas som känsliga data eftersom det kan utnyttjas av någon med skadlig avsikt för att få information om hur servrar distribueras och konfigureras i din miljö. Mer information finns i avsnittet om att [allokera GUID i PowerShell Desired State Configuration pull-läge](https://devblogs.microsoft.com/powershell/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Planerings uppgift

- Vem kommer att ansvara för att kopiera konfigurationer till pull-servermappen när de är klara?
- Vad kommer processen att bli av om konfigurationer har skapats av ett program team?
- Kommer du att använda en lagrings plats för att lagra konfigurationer när de skapas, i flera team?
- Automatiseras processen med att kopiera konfigurationer till servern och skapa en kontroll Summa när de är klara?
- Hur mappar du GUID till servrar eller roller och var kommer det att lagras?
- Vad ska du använda som en process för att konfigurera klient datorer och hur kommer det att integreras med processen för att skapa och lagra konfigurations-GUID?

## <a name="installation-guide"></a>Installationsguide

*Skript som anges i det här dokumentet är stabila exempel. Granska alltid skript noggrant innan du kör dem i en produktions miljö.*

### <a name="prerequisites"></a>Förutsättningar

Använd följande kommando för att kontrol lera versionen av PowerShell på servern.

```powershell
$PSVersionTable.PSVersion
```

Uppgradera om möjligt till den senaste versionen av Windows Management Framework. Hämta sedan `xPsDesiredStateConfiguration` modulen med hjälp av följande kommando.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Kommandot ber om ditt godkännande innan du laddar ned modulen.

### <a name="installation-and-configuration-scripts"></a>Installations-och konfigurations skript

Den bästa metoden för att distribuera en DSC-pull-server är att använda ett DSC-konfigurations skript. Det här dokumentet visar skript, inklusive både grundläggande inställningar som endast konfigurerar DSC-webbtjänsten och avancerade inställningar som konfigurerar en Windows Server från slut punkt till slut punkt inklusive DSC-webbtjänst.

Obs: för närvarande `xPSDesiredStateConfiguration` kräver DSC-modulen att servern är en-US-språkvariant.

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
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
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

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
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

### <a name="verify-pull-server-functionality"></a>Verifiera hämtning av Server funktioner

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
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

Det här exemplet visar hur du manuellt initierar en klient anslutning (kräver WMF5) för testning.

```powershell
Update-DscConfiguration –Wait -Verbose
```

Cmdlet: en [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) används för att lägga till en typ CNAME-post i en DNS-zon.

PowerShell-funktionen för att [skapa en kontroll summa och publicera DSC MOF till SMB pull server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genererar automatiskt den nödvändiga kontroll summan och kopierar sedan både MOF-konfigurationen och kontroll summornas filer till SMB-pull-servern.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Tillägg – förstå ODATA-tjänstens data fil typer

En datafil lagras för att skapa information under distributionen av en pull-server som inkluderar OData-webbtjänsten. Vilken typ av fil som används beror på operativ systemet, enligt beskrivningen nedan.

- **Windows Server 2012** – filtypen är alltid `.mdb`
- **Windows Server 2012 R2** – filtypen används som standard `.edb` om inte en `.mdb` anges i konfigurationen

I det [avancerade exempel skriptet](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) för att installera en hämtnings server hittar du också ett exempel på hur du automatiskt kontrollerar web.config fil inställningarna för att förhindra eventuella fel som orsakas av filtypen.
