---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Hämta server bästa praxis"
ms.openlocfilehash: 045f98475d6182b329ecf048038a98e933684a82
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="pull-server-best-practices"></a>Hämta server bästa praxis

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Sammanfattning: Det här dokumentet är avsett att inkludera processen och utökningsbarhet att hjälpa tekniker som förbereder för lösningen. Information bör ge bästa praxis som identifieras av kunder och sedan verifieras av Produktteamet för att säkerställa rekommendationer framtida riktade och anses vara stabil.

| |Doc-Info|
|:---|:---|
författare | Michael Greene  
Granskare | Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic  
Publicerade | April 2015

## <a name="abstract"></a>Abstrakt

Det här dokumentet är utformad att ge officiella vägledning för alla planera för en Windows PowerShell Desired State Configuration pull-serverimplementering. En pull-server är en enkel tjänst som tar endast minuter att distribuera. Även om det här dokumentet kommer att erbjuda teknisk vägledning som kan användas i en distribution, är värdet för det här dokumentet som en referens för bästa praxis och vad du ska tänka på innan du distribuerar.
Läsare bör ha grundläggande kunskaper med DSC och de termer som används för att beskriva komponenterna som ingår i en DSC-distribution. Mer information finns i [Windows PowerShell Desired Configuration översikt över](https://technet.microsoft.com/en-us/library/dn249912.aspx) avsnittet.
Som DSC är förväntat att utvecklas i molnet takt förväntas också den underliggande tekniken inklusive hämtningsservern att utvecklas och ger nya möjligheter. Det här dokumentet innehåller en versionstabell i tillägget som innehåller referenser till tidigare versioner och referenser till framtida söker lösningar för att uppmuntra framtida Designer.

Det här dokumentet två huvuddelar:

 - Planera konfiguration
 - Installationsguiden
 
### <a name="versions-of-the-windows-management-framework"></a>Versioner av Windows Management Framework 
Informationen i det här dokumentet är avsedd att tillämpa på Windows Management Framework 5.0. WMF 5.0 inte krävs för distribution och drift av en pull-server, är version 5.0 fokus för det här dokumentet.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell önskad Tillståndskonfiguration
Önskat tillstånd Configuration (DSC) är en plattform som gör att distribuera och hantera konfigurationsdata med hjälp av en branschen syntax som heter Managed Object Format (MOF) för att beskriva Common Information Model (CIM). Det finns ett projekt med öppen källkod, Open Management Infrastructure (OMI), för att ytterligare utvecklingen av dessa normer över plattformar, inklusive Linux och -maskinvara, operativsystem. Mer information finns i [DMTF sida länkar till MOF-specifikationer](http://dmtf.org/standards/cim), och [OMI dokument och källan](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell innehåller en uppsättning tillägg för Desired State Configuration som du kan använda för att skapa och hantera deklarativ konfigurationer.

### <a name="pull-server-role"></a>Pull-serverrollen  
En pull-server är en centraliserad tjänst för att lagra konfigurationer som kommer att vara tillgänglig för målnoder.
 
Pull-serverrollen kan distribueras som en webbserver-instans eller en SMB filresurs. Web server-kapacitet innehåller ett OData-gränssnitt och att inkludera välja funktioner för målnoder rapporterar bekräftelse av lyckats eller misslyckats eftersom konfigurationer tillämpas. Den här funktionen är användbar i miljöer där det finns ett stort antal målnoder. När du har konfigurerat en målnod (kallas även en klient) för att peka på hämtningsservern i den senaste konfigurationen hämtas och aktiveras data och alla nödvändiga skript. Detta kan inträffa som en enstaka distribution eller som ett nytt förekommer jobb som är dessutom hämtningsservern i en viktig tillgång för att hantera ändring i större skala. Mer information finns i [Windows PowerShell önskad tillstånd hämtar Konfigurationsservrar](https://technet.microsoft.com/en-us/library/dn249913.aspx) och [Push och Pull-konfigurationslägen](https://technet.microsoft.com/en-us/library/dn249913.aspx).

## <a name="configuration-planning"></a>Planera konfiguration

För alla företag programdistribution finns information som samlas in i förväg för att planera för rätt arkitektur och förberedas för de steg som krävs för att slutföra distributionen. Följande avsnitt innehåller information om hur du förbereder och de organisatoriska anslutningar som behöver förmodligen inträffa i förväg.

### <a name="software-requirements"></a>Programvarukrav

Distribution av en pull-server kräver funktionen DSC-tjänsten i Windows Server. Den här funktionen introducerades i Windows Server 2012 och har uppdaterats via pågående versioner av Windows Management Framework (WMF).

### <a name="software-downloads"></a>Nedladdning av programvara

Förutom att installera det senaste innehållet från Windows Update finns två hämtningar anses vara bästa praxis för att distribuera en DSC pull-server: den senaste versionen av Windows Management Framework och en DSC-modul för att automatisera etablering av pull-servrar.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 innehåller en funktion som heter DSC-tjänsten. Funktionen DSC-tjänsten tillhandahåller pull serverfunktionalitet, inklusive de binära filerna som har stöd för OData-slutpunkten. WMF ingår i Windows Server och uppdateras i en flexibel takt mellan versioner av Windows Server. [Nya versioner av WMF 5.0](http://aka.ms/wmf5latest) kan innehålla uppdateringar till funktionen DSC-tjänsten. Därför är det bäst att hämta den senaste versionen av WMF och granska viktig information för att avgöra om versionen innehåller en uppdatering av funktionen DSC-tjänsten. Du bör också granska avsnittet i viktig information som anger om den design för en uppdatering eller scenario statusen stabilt och experiment. Om du vill tillåta en smidig övergång cykel enskilda funktioner kan deklareras stabil, är vilket anger att funktionen redo att användas i en produktionsmiljö, även när WMF släpps i förhandsgranskningen.
Andra funktioner som tidigare har uppdaterats av WMF versioner (se WMF viktig information för detaljerat):

 - Windows PowerShell, Windows PowerShell Integrated Scripting
 - Environment (ISE) Windows PowerShell-webbtjänster (Management OData
 - IIS-tillägg) Windows PowerShell önskad Tillståndskonfiguration DSC)
 - Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC-resurs

En pull-serverdistribution kan förenklas genom att etablera tjänsten med hjälp av ett DSC-konfigurationsskript. Det här dokumentet innehåller konfigurationsskript som kan användas för att distribuera en klar servernoden i produktion. Om du vill använda konfigurationsskript en DSC-modul krävs som inte ingår i Windows Server. Nödvändiga Modulnamn **xPSDesiredStateConfiguration**, som innehåller resursen DSC **xDscWebService**. Modulen xPSDesiredStateConfiguration kan hämtas [här](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Använd den **installera modulen** cmdlet från den **PowerShellGet** modul.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Den **PowerShellGet** modulen hämtar modulen: 

`C:\Program Files\Windows PowerShell\Modules`

Planera aktivitet|
---|
Du har tillgång till installationsfilerna för Windows Server 2012 R2?|
Distributionsmiljö har Internetåtkomst för att hämta WMF och modulen från galleriet online?|
Hur ska du installera de senaste säkerhetsuppdateringarna när du har installerat operativsystemet?|
Miljön har Internetåtkomst för att hämta uppdateringar eller den har en lokal server i Windows Server Update Services (WSUS)?|
Har du tillgång till installationsfilerna för Windows Server som redan omfattar uppdateringar via offline injection?|

### <a name="hardware-requirements"></a>Maskinvarukrav

Pull-serverdistribution stöds på både fysiska och virtuella servrar. Storlek för kraven på hämtningsservern överensstämmer med kraven för Windows Server 2012 R2.

Processor: 1,4 GHz 64-bitars processor  
Minne: 512 MB  
Diskutrymme: 32 GB  
: Gigabit Ethernet-nätverkskort  

Planera aktivitet|
---|
Du distribuerar på fysisk maskinvara eller på en virtualiseringsplattform?|
Vad är processen för att begära en ny server för målmiljön?|
Vad är den genomsnittliga tid för en server ska bli tillgänglig?|
Vilken storlek du begär servern?|

### <a name="accounts"></a>Konton

Det finns inga krav på tjänstkonto att distribuera en pull-serverinstans. Det finns emellertid scenarier där webbplatsen kan köras i kontexten för ett lokalt användarkonto. Till exempel om det är nödvändigt att åtkomst en storage-resurs för webbplatsens innehåll och Windows Server eller enhet som är värd för storage-resurs är inte ansluten till en domän.

### <a name="dns-records"></a>DNS-poster

Du behöver ett servernamn som du använder när du konfigurerar klienter för att arbeta med en pull-servermiljö. I testmiljöer, oftast serverns värdnamn eller IP-adressen för servern kan användas om DNS-namnmatchningen inte är tillgänglig. Det bästa sättet är att skapa en DNS CNAME-post i produktionsmiljöer eller i en testmiljö som är avsedd att representera en Produktionsdistribution.

Ett DNS CNAME kan du skapa ett alias du vill referera till din värd (A) post. Syftet med den ytterligare namnposten är att öka flexibiliteten ändras inte behövs i framtiden. En CNAME-post kan hjälpa för att isolera klientkonfigurationen så att ändringar av server-miljö, t.ex ersätter en pull-server eller lägga till ytterligare pull-servrar, inte kräver en motsvarande ändring i klientkonfigurationen.

Tänk lösningsarkitekturen när du väljer ett namn för DNS-posten. Om med belastningsutjämning, måste certifikatet som används för att skydda trafik via HTTPS delar samma namn som DNS-posten. 

Scenario |Bästa praxis
:---|:---
Testmiljö |Återskapa planerad produktionsmiljön, om möjligt. Ett värdnamn för servern är lämpligt för enkel konfigurationer. Om DNS inte är tillgänglig, kan en IP-adress användas i stället för ett värdnamn.|
Distribution av enskild nod |Skapa en DNS CNAME-post som pekar på serverns värdnamn.|

Mer information finns i [konfigurera DNS för resursallokering i Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).

Planera aktivitet|
---|
Vet du att kontakta om du vill att DNS-poster skapas och ändras?|
Vad är den genomsnittliga tid en begäran om en DNS-post?|
Behöver du begära statiska värdnamn (A)-poster för servrar?|
Vad du begär som en CNAME-post?|
Om det behövs, vilken typ av belastningsutjämning lösning ska du använda? (se avsnittet belastningsutjämning för information)|

### <a name="public-key-infrastructure"></a>Infrastruktur för offentliga nycklar

De flesta organisationer kräver idag att nätverkstrafik, särskilt trafik som innehåller dessa känsliga data om hur servrar har konfigurerats, måste verifieras och krypterad under överföringen. När det är möjligt att distribuera en pull-server med hjälp av HTTP som underlättar klientbegäranden i klartext, är det en bra idé att skydda trafik med hjälp av HTTPS. Tjänsten kan konfigureras för att använda HTTPS med en uppsättning parametrar i DSC-resursen **xPSDesiredStateConfiguration**.

Certifikatkrav för säker HTTPS-trafik för pull-servern är inte annat än att skydda alla andra HTTPS-webbplats. Den **webbservern** mallen i Certifikattjänster i Windows Server uppfyller de nödvändiga funktionerna.

Planera aktivitet|
---|
Om certifikatbegäran inte sker automatiskt, som behöver du kontakta ett certifikat på begäran?|
Vad är den genomsnittliga tid för begäran?|
Hur certifikatfilen överförs till dig?|
Hur certifikatets privata nyckel överförs till dig?|
Hur lång tid är förfallotiden som standard?|
Har du lösas på ett DNS-namn för pull-servermiljö, som du kan använda för certifikatets namn?|

### <a name="choosing-an-architecture"></a>Om du väljer en arkitektur

En pull-server kan distribueras med hjälp av antingen en webbtjänst som IIS eller en SMB filresurs. I de flesta fall är ger web service alternativet större flexibilitet. Det är inte ovanligt att HTTPS-trafik färdas över nätverksgränser, medan SMB-trafik är ofta filtrerade eller blockeras mellan nätverk. Webbtjänsten ger också möjlighet att inkludera en överensstämmelse Server eller Web Reporting Manager (både ämnen tas upp i en framtida version av det här dokumentet) som tillhandahåller en mekanism för klienter för att rapportera status tillbaka till en server för centraliserad synlighet. SMB ger ett alternativ för miljöer där principen anger att en server inte kan användas och för andra miljökrav som gör en rollen som webbserver oönskade. Kom ihåg att utvärdera kraven för signering och kryptering av trafik i båda fallen. Är alla alternativ vara värt att hänsyn tagits till HTTPS, SMB-signering och IPSEC-principer.

#### <a name="load-balancing"></a>Belastningsutjämning  
Klienter som interagerar med webbtjänsten gör en begäran om information som returneras i ett enda svar. Inga sekventiella förfrågningar krävs, så det inte är nödvändigt för belastningsutjämning plattform för att säkerställa sessioner underhålls på en enskild server när som helst i tid.

Planera aktivitet|
---|
Vilken lösning ska användas för belastningsutjämning trafik mellan servrar?|
Om du använder en maskinvarubaserad belastningsutjämnare som tar en begäran om att lägga till en ny konfiguration för enheten?|
Vad är den genomsnittliga tid för en begäran om att konfigurera en ny belastning belastningsutjämnade webbtjänsten?|
Vilken information kommer att krävas för begäran?|
Du måste begära en ytterligare IP-adress eller gruppen som ansvarar för belastningsutjämning hanterar som?|
Har du DNS-poster som behövs och det krävs av gruppen som ansvarar för att konfigurera nätverkslösning för belastningsutjämning?|
Läsa in belastningsutjämning lösningen kräver att PKI ska hanteras av enheten eller kan den belastningsutjämna HTTPS-trafik, så länge det finns inga sessionskrav?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Mellanlagring av konfigurationer och moduler på hämtningsservern

Som en del av konfigurationen planering, behöver du tycker om vilka DSC-moduler och konfigurationer som kommer att finnas av pull-servern. För att planera konfigurationen är det viktigt att ha en grundläggande förståelse för hur du förbereder och distribuerar innehåll till en pull-server. 

Det här avsnittet kommer i framtiden, expanderas och ingår i en Funktionsguide för DSC Pull-Server.  Guiden diskuterar dagliga processen för att hantera moduler och konfigurationer över tid med automatisering. 

#### <a name="dsc-modules"></a>DSC-moduler  
Klienter som begär en konfiguration måste DSC-moduler som krävs. En funktion av pull-server är att automatisera distribution på begäran av DSC-moduler till klienter. Om du distribuerar en pull-server för första gången, kanske som ett labb eller konceptbevis, ska du troligen är beroende av DSC-moduler som är tillgängliga från offentliga databaser, till exempel PowerShell-galleriet eller PowerShell.org GitHub-lagringsplatser för DSC-moduler .

Det är viktigt att komma ihåg att även för tillförlitliga online källor, till exempel PowerShell-galleriet alla moduler som har hämtats från en offentlig databas bör granskas av någon med PowerShell upplevelse och kunskap om miljön där modulerna som kommer att använda före som används i produktionen. Det är dags att söka efter eventuella ytterligare nyttolast i modulen som kan tas bort, till exempel dokumentation och exempel skript för att slutföra den här uppgiften. Detta minskar nätverkets bandbredd per klient i sin första begäran när moduler ska laddas ned över nätverket från servern till klienten.

Varje modul måste paketeras i ett specifikt format, en ZIP-fil med namnet ModuleName_Version.zip som innehåller modulen nyttolasten. När filen kopieras till servern måste du skapa en fil kontrollsummor. När klienter ansluter till servern, används kontrollsumman som för att kontrollera innehållet i DSC-modulen inte har ändrats sedan den publicerades.

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

Planera aktivitet|
---|
Om du planerar en test- eller labb-miljö är vilka scenarier för att verifiera?|
Finns det offentligt tillgängliga modulerna som innehåller resurser för att omfatta allt du behöver eller behöver du skapa dina egna resurser?|
Kommer din miljö ha Internetåtkomst för att hämta offentlig moduler?|
Vem är ansvarig för att granska DSC-moduler?|
Om du planerar en produktionsmiljö vad ska du använda som en lokal databas för lagring av DSC-moduler?|
En central team accepterar DSC-moduler från programteam? Vad är processen?|
Kan du automatisera paketering, kopiera och skapa en kontrollsumma för produktionsklara DSC-moduler på servern från käll-lagringsplatsen?|
Ditt team ansvarar för att hantera plattformen automation?|

#### <a name="dsc-configurations"></a>DSC-konfigurationer

Syftet med en pull-server är att tillhandahålla en centraliserad mekanism för att distribuera DSC-konfigurationer för klientnoder. Konfigurationerna som lagras på servern som MOF-dokument. Varje dokument kommer att namnges med ett unikt GUID. När klienterna är konfigurerade för att ansluta till en pull-server, ges de också GUID för konfigurationen hon måste begära. Systemet för att referera till konfigurationer av GUID garanterar globala unika och är flexibel så att du kan använda en konfiguration med granularitet per nod eller som en rollkonfiguration som sträcker sig över flera servrar som ska ha identiska konfigurationer.

#### <a name="guids"></a>GUID

Planera för konfiguration GUID är värt att ytterligare åtgärder när du funderar på en pull-serverdistribution. Det finns inga särskilda krav för hur du hanterar GUID och processen kan förväntas vara unikt för varje miljö. Processen kan variera mellan enkla och komplexa: en centralt lagrade CSV-fil, en enkel SQLtabell, ett CMDB eller en komplex lösning kräver integrering med en annan lösning för verktyget eller programvara. Det finns två sätt:

 - **Tilldela GUID per server** – ger ett mått på försäkran om att varje konfiguration kontrolleras separat. Detta ger en precision runt uppdateringar och kan fungera bra i miljöer med några servrar.
 - **Tilldela GUID per serverrollen** – alla servrar som utför samma funktion, till exempel webbservrar, använda samma GUID för att referera till den nödvändiga konfigurationsdatan.  Tänk på att om många servrar som delar samma GUID, alla skulle uppdateras samtidigt när konfigurationen ändras.

GUID är något som bör övervägas känsliga data eftersom den kan utnyttjas av en användare med skadliga åtgärder för att få intelligence om hur servrar distribuerats och konfigurerats i din miljö. Mer information finns i [på ett säkert sätt allokera GUID i PowerShell önskad tillstånd Pull-konfigurationsläge](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).

Planera aktivitet|
---|
Vem är ansvarig för att kopiera konfigurationer i till mappen pull server när de är klara?|
Om konfigurationer som skapats av en grupp av program, vad processen är att lämnar dem?|
Använder du en lagringsplats för konfigurationer som de som skapats, mellan olika grupper?|
Kan du automatisera processen för att kopiera konfigurationer till servern och skapa en kontrollsumma när de är klara?|
Hur du mappar GUID till servrar eller roller och där det sparas?|
Vad ska du använda som en process för att konfigurera klientdatorer och hur kan den integreras med processen skapar och lagrar Configuration GUID?|

## <a name="installation-guide"></a>Installationsguiden

*Skript som anges i det här dokumentet är stabil exempel. Alltid läsa igenom skript noggrant innan du kör dem i en produktionsmiljö.*

### <a name="prerequisites"></a>Förutsättningar

Använd följande kommando för att kontrollera version av PowerShell på servern.

```powershell
$PSVersionTable.PSVersion
```

Om det är möjligt att uppgradera till den senaste versionen av Windows Management Framework.
Sedan hämtar den `xPsDesiredStateConfiguration` modul med följande kommando.


```powershell
Install-Module xPSDesiredStateConfiguration
```

Kommandot begär ditt godkännande innan du hämtar modulen.

### <a name="installation-and-configuration-scripts"></a>Skript för installation och konfiguration
-

Det bästa sättet att distribuera en DSC pull-server är att använda ett DSC-konfigurationsskript. Det här dokumentet visas skript inklusive både grundläggande inställningar som konfigurerar bara DSC-webbtjänsten och avancerade inställningar som konfigurerar en Windows Server slutpunkt till slutpunkt inklusive DSC webbtjänst.

Obs: För närvarande den `xPSDesiredStateConfiguation` DSC-modulen kräver att servern ska vara EN-US lokalisering.

### <a name="basic-configuration-for-windows-server-2012"></a>Grundläggande konfiguration för Windows Server 2012
-------------------------------------------
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
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN' 

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


## <a name="additional-references-snippets-and-examples"></a>Ytterligare referenser, kodavsnitt och exempel

Det här exemplet visar hur du manuellt initiera en klientanslutning (kräver WMF5) för testning. 

```powershell
Update-DSCConfiguration –Wait -Verbose
```

Den [Lägg till DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet som används för att lägga till en typ CNAME-post till en DNS-zon. 

PowerShell-funktionen för att [skapa en kontrollsumma och publicera DSC MOF till SMB-Pull Server](http://bit.ly/1E46BhI) genererar automatiskt krävs kontrollsumma och kopierar sedan både MOF-konfigurationen och kontrollsumma filer till pull SMB-servern.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Tillägg – förstå ODATA service data filtyper

En fil lagras för att skapa information vid distribution av en pull-server som innehåller OData-webbtjänst. Typ av fil beror på operativsystemet, enligt beskrivningen nedan.

 - **Windows Server 2012**  
Filtypen kommer alltid att .mdb
 - **Windows Server 2012 R2**  
Filtypen kommer som standard edb om en .mdb har angetts i konfigurationen

I den [avancerade exempelskriptet](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) för att installera en Pull-Server, det finns även ett exempel på hur du styr inställningarna för web.config-filen för att förhindra alla risken för fel som orsakats av filtyp automatiskt.

