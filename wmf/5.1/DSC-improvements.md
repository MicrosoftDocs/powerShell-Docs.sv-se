---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: DSC-förbättringar i WMF 5.1
ms.openlocfilehash: 32bdde6d43d17cc76c454fe10b00097753a9eebe
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309550"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Förbättringar i Desired State Configuration (DSC) i WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Förbättringar av DSC-klassen resurs

Vi har löst följande kända problem i WMF 5.1:

- Get-DscConfiguration kan returnera tomma värden (null) eller fel om en komplex/hash-tabelltyp returneras av Get()-funktionen för en klass-baserade DSC-resurs.
- Get-DscConfiguration returnerar fel om RunAs-autentiseringsuppgift används i DSC-konfigurationen.
- Klass-baserade resursen kan inte användas i en sammansatt konfiguration.
- Start-DscConfiguration låser sig om klass-baserade resursen har en egenskap för sin egen typ.
- Klass-baserade resursen kan inte användas som en exklusiv resurs.

## <a name="dsc-resource-debugging-improvements"></a>DSC-resurs felsökning förbättringar

I WMF 5.0 stoppades PowerShell felsökningsprogrammet inte på klass-baserade resurs-metoden (Get och Set/testning) direkt.
WMF 5.1 slutar felsökningsprogrammet vid klass-baserade resurs-metod på samma sätt som för MOF-baserade resurser metoder.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC pull-klienten har stöd för TLS 1.1 och TLS 1.2

Tidigare stöds DSC pull-klienten endast SSL3.0 och TLS1.0 över HTTPS-anslutningar.
När tvungen att använda säkrare protokoll, skulle pull-klienten sluta fungera.
I WMF 5.1 DSC pull klienten inte längre har stöd för SSL 3.0 och lägger till stöd för protokollen säkrare TLS 1.1 och TLS 1.2.

## <a name="improved-pull-server-registration"></a>Registrera för förbättrad pull-servern

I tidigare versioner av WMF skulle samtidiga registreringar/rapportering begäranden till DSC pull-servern när du använder ESENT-databasen leda till MGM om du inte kan registrera och/eller rapportera.
I sådana fall händelseloggarna på hämtningsservern har felet ”instansnamnet används redan”.
Detta beror på ett felaktigt mönster som används för att få åtkomst till ESENT-databasen i ett flertrådat scenario.
Det här problemet har åtgärdats i WMF 5.1.
Samtidiga registreringar eller rapportering (som involverar ESENT databasen) fungerar bra i WMF 5.1.
Det här problemet gäller endast för ESENT-databasen och gäller inte för OLEDB-databasen.

## <a name="enable-circular-log-on-esent-database-instance"></a>Aktivera cirkulär inloggning ESENT-databasinstans

I eariler versionen av DSC-PullServer, ESENT loggfiler fyller upp diskutrymme på den pullserver becouse databasinstansen skapades utan cirkulär loggning. I den här versionen har du möjlighet att styra instansen med hjälp av web.config i pullserver cirkulär loggning. Som standard anges CircularLogging till SANT.

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a>Hämta partiella configuration namngivningskonvention

I den tidigare versionen har en partiell konfiguration namngivningskonvention att MOF-filens namn i pull/tjänsten server ska matcha partiella Konfigurationsnamnet anges i inställningarna för lokala configuration manager som i sin tur måste matcha den Konfigurationsnamnet inbäddade i MOF-filen.

Se ögonblicksbilder nedan:

- Lokala konfigurationsinställningar som definierar en partiell konfiguration som en nod kan ta emot.

![Exempel metakonfigurationen](../images/MetaConfigPartialOne.png)

- Exempel partiella konfigurationsdefinition

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- 'ConfigurationName' inbäddade i genererade MOF-filen.

![Exempel genererade mof-filen](../images/PartialGeneratedMof.png)

- Filnamn i databasen för pull-konfiguration

![Filnamn i konfiguration av databas](../images/PartialInConfigRepository.png)

Azure Automation-tjänstnamnet genereras MOF-filer som `<ConfigurationName>.<NodeName>.mof`.
Konfigurationen nedan sammanfattar så att PartialOne.localhost.mof.

Detta har gjort det omöjligt att dra en partiell konfigurationen från Azure Automation-tjänsten.

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

I WMF 5.1 en partiell konfiguration i pull/tjänsten server kan namnges som `<ConfigurationName>.<NodeName>.mof`.
Om en dator är att använda en enda konfigurationen från en pull kan dessutom/servertjänsten sedan konfigurationsfilen på pull server configuration databasen ha ett filnamn.
Namngivning flexibilitet kan du hantera noderna delvis av Azure Automation-tjänsten, där vissa konfigurationsinställningar för noden kommer från Azure Automation DSC och med en partiell konfiguration som du hanterar lokalt.

Metakonfigurationen nedan ställer in en nod ska hanteras både lokalt som med Azure Automation-tjänsten.

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Med hjälp av PsDscRunAsCredential med sammansatta DSC-resurser

Vi har lagt till stöd för användning av [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) med DSC [sammansatta](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resurser.

Du kan ange ett värde för PsDscRunAsCredential när du använder sammansatta resurser inuti konfigurationer.
När anges körs alla resurser i en sammansatt resurs som en RunAs-användare.
Om en sammansatt resurs anrop till en annan sammansatta resurs kan köra alla dess resurser även som RunAs-användare.
RunAs-autentiseringsuppgifterna sprids till valfri nivå i hierarkin sammansatta resurs.
Om en resurs i en sammansatt resurs anger sitt eget värde för PsDscRunAsCredential, resulterar en merge-fel under kompilering av konfiguration.

Det här exemplet visar användningen med [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) sammansatta resurs som ingår i PSDesiredStateConfiguration modulen.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a>DSC-modulen och signering verifieringar-konfiguration

I DSC distribueras konfigurationer och moduler till hanterade datorer från hämtningsservern i.
Om pull-servern har komprometterats bör en angripare ändra konfigurationer och moduler på hämtningsservern potentiellt och har distribuerats till alla hanterade noder, kompromettera alla.

I WMF 5.1 DSC stöder verifierar digitala signaturer i katalogen och konfiguration (. MOF)-filer.
Den här funktionen förhindrar att noder körning konfigurationer eller modulen filer som inte har signerats av en betrodd undertecknare eller som har ändrats efter att de har signerats av betrodda undertecknare.

### <a name="how-to-sign-configuration-and-module"></a>Hur du registrerar konfiguration och modulen

***
* Konfigurationsfiler (. MOF-filer): befintliga PowerShell-cmdleten [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) är utökat stöd för signering av MOF-filer.
* Moduler: Signering av moduler görs genom att registrera den motsvarande modul-katalog med följande steg:
    1. Skapa en katalogfil: en katalogfil innehåller en uppsättning kryptografiska hash-värden eller tumavtryck.
       Varje tumavtrycket motsvarar en fil som ingår i modulen.
       Följande nya cmdlet [ny FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), har lagts till kan du skapa en katalogfil för sina modulen.
    2. Signera katalogfilen: Använd [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) att signera katalogfilen.
    3. Placera katalogfilen i mappen som modulen.
Enligt konventionen är placeras modulen katalogfil under mappen modulen med samma namn som modulen.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>LocalConfigurationManager inställningar för att aktivera signering verifieringar

#### <a name="pull"></a>Hämtar

LocalConfigurationManager för en nod utför signering validering av moduler och konfigurationer baserat på de aktuella inställningarna.
Signaturverifiering är inaktiverat som standard.
Signaturverifiering kan aktiveras genom att lägga till blockeringen 'SignatureValidation' meta-konfigurationsdefinition för noden som visas nedan:

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

Anger ovan metakonfigurationen på en nod kan verifiera signaturen på hämtade konfigurationer och moduler.
Local Configuration Manager utför följande steg för att verifiera de digitala signaturerna.

1. Verifiera signaturen på en konfigurationsfil (. MOF) är giltig.
   Den använder du PowerShell-cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), som utökas i 5.1 att stödja MOF signaturverifiering.
2. Kontrollera som auktoriserad undertecknarens certifikatutfärdaren är betrodd.
3. Hämta modul/resursberoenden av konfigurationen till en tillfällig plats.
4. Verifiera signaturen på den katalog som ingår i modulen.
    * Hitta en `<moduleName>.cat` och kontrollera att signaturen med hjälp av cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Kontrollera den certifikatutfärdare som autentiseras undertecknarens är betrodd.
    * Kontrollera innehållet i modulerna som inte har ändrats med nya cmdlet [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Installera modulen till $env: ProgramFiles\WindowsPowerShell\Modules\
6. Processkonfiguration

> Obs: Signaturverifiering på modul-katalog och konfiguration utförs endast när konfigurationen tillämpas i systemet för första gången eller när modulen hämtas och installeras.
Konsekvenskontroll körs validerar inte signaturen för Current.mof eller dess beroenden i modulen.
Om det gick inte att verifiera när som helst, till exempel om konfigurationen hämtas från pull-servern är osignerat, sedan bearbetning av konfigurationen avslutas med felet visas nedan och alla temporära filer tas bort.

![Exempelkonfiguration fel utdata](../images/PullUnsignedConfigFail.png)

På liknande sätt kan signerat dra en modul vars katalogen inte är resulterar i följande fel:

![Exempel Felmodulen för utdata](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

En konfiguration som levereras med hjälp av push kan vara har manipulerats på källan innan det levereras till noden.
Local Configuration Manager utför liknande steg för verifiering av signatur för intryckt eller publicerade konfiguration(er).
Nedan visas en komplett exempel på signaturvalidering för distribution.

- Aktivera signaturverifiering på noden.

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- Skapa en exempelfil i konfigurationen.

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- Försök att överföra osignerade konfigurationsfilen till noden.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Logga konfigurationsfilen med kodsigneringscertifikat.

![SignMofFile](../images/SignMofFile.png)

- Försök att överföra den signerade MOF-filen.

![SignMofFile](../images/PushSignedMof.png)
