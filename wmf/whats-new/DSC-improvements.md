---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: DSC-förbättringar i WMF 5.1
ms.openlocfilehash: e7f20bfa865777aeac8f083959782317cfdf6cde
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856233"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Förbättringar i Desired State Configuration (DSC) i WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Förbättringar av DSC-klass resurs

Vi har åtgärdat följande kända problem i WMF 5.1:

- Get-DscConfiguration kan returnera tomma värden (null) eller om en komplex/hash-tabelltyp returneras av Get() funktion för en klassbaserade DSC-resurs.
- Get-DscConfiguration returnerar fel om RunAs-autentiseringsuppgift används i DSC-konfiguration.
- MOF-baserade resursen kan inte användas i en sammansatt konfiguration.
- Start-DscConfiguration låser sig om MOF-baserade resurs har en egenskap för sin egen typ.
- MOF-baserade resursen kan inte användas som en exklusiv resurs.

## <a name="dsc-resource-debugging-improvements"></a>Felsökningsförbättringar för DSC-resurs

I WMF 5.0 stoppades PowerShell-felsökare inte på klass-baserad resurs-metoden (Get/Set/Test) direkt. I WMF 5.1 stoppar felsökningsprogrammet vid MOF-baserade resurs-metod på samma sätt som för MOF-baserade resurser metoder.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC pull-klienten har stöd för TLS 1.1 och TLS 1.2

Tidigare stöds hämtningsklient DSC endast SSL3.0 och TLS 1.0 över HTTPS-anslutningar. När du tvungen att använda säkrare protokoll, skulle pull-klienten sluta fungera. I WMF 5.1 DSC pull klienten inte längre har stöd för SSL 3.0 och lägger till stöd för protokollen säkrare TLS 1.1 och TLS 1.2.

## <a name="improved-pull-server-registration"></a>Förbättrad pull-serverregistrering

I tidigare versioner av WMF skulle samtidiga registreringar/reporting begäranden till en DSC-hämtningsserver när du använder ESENT-databasen leda till LCM som inte kan registrera och/eller rapport. I sådana fall kan händelseloggarna på hämtningsservern har felet ”instansnamnet används redan”. Detta beror på ett felaktigt mönster som används för att få åtkomst till ESENT-databasen i ett scenario med flera trådar. Det här problemet har åtgärdats i WMF 5.1. Samtidiga registreringar eller rapporter (som involverar ESENT-databas) fungerar bra i WMF 5.1. Det här problemet gäller endast för ESENT-databasen och gäller inte för OLEDB-databasen.

## <a name="enable-circular-log-on-esent-database-instance"></a>Aktivera cirkulär inloggning ESENT-databasinstans

I eariler versioner av DSC-PullServer ESENT loggfiler fyller upp diskutrymme på den pullserver becouse databasinstansen som skapades utan cirkulär loggning. I den här versionen har du möjlighet att styra den instansen med web.config i pullserver cirkulär loggning. Som standard anges CircularLogging till TRUE.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>WOW64-stöd för Konfigurationsnyckelord

Den `Configuration` nyckelordet stöds nu i WOW64 på en 64-bitars dator. Det innebär att en DSC-konfiguration kan definieras och kompileras i en 32-bitars process, till exempel Windows PowerShell ISE (x 86) som körs på en 64-bitars dator.

## <a name="pull-partial-configuration-naming-convention"></a>Hämta namngivningskonvention för partiell konfiguration

I den föregående versionen Namngivningskonventionen för en partiell konfiguration var att MOF-filnamnet i pull-server/tjänsten måste matcha namnet partiell konfiguration i de lokala configuration manager-inställningar som i sin tur måste matcha den namn på inbäddade i MOF-filen.

Se ögonblicksbilder nedan:

- Lokala konfigurationsinställningar som definierar en partiell konfiguration som en nod kan ta emot.

  ![Exemplet metaconfiguration](../images/MetaConfigPartialOne.png)

- Partiell konfiguration exempeldefinition

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

- {ConfigurationName} inbäddad i den genererade MOF-filen.

  ![Exemplet genererade mof-filen](../images/PartialGeneratedMof.png)

- Filnamn i pull-konfigurationsdatabasen

  ![Filnamn i konfiguration av databas](../images/PartialInConfigRepository.png)

  Azure Automation-tjänstnamn genereras MOF-filer som `<ConfigurationName>.<NodeName>.mof`. Av konfigurationen nedan kompilerar så att PartialOne.localhost.mof.

  Detta har gjort det omöjligt att pull en partiell konfigurationen från Azure Automation-tjänsten.

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

  I WMF 5.1 kan en partiell konfiguration i pull-server/tjänsten namnges som `<ConfigurationName>.<NodeName>.mof`. Om en dator är att hämta en enda konfiguration från en pull ha/servertjänsten sedan konfigurationsfilen på konfigurationsdatabasen för pull-server dessutom valfritt filnamn. Den här namngivning flexibiliteten kan du hantera dina noder delvis av Azure Automation-tjänsten var konfiguration till noden kommer från Azure Automation DSC och med en partiell konfiguration som du hanterar lokalt.

  Metaconfiguration nedan ställer in en nod ska hanteras både lokalt samt av Azure Automation-tjänsten.

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Med hjälp av PsDscRunAsCredential med DSC sammansatta resurser

Vi har lagt till stöd för användning av [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) med DSC [sammansatta](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resurser.

Du kan nu ange ett värde för **PsDscRunAsCredential** när du använder sammansatta resurser inuti konfigurationer. När du anger körs alla resurser i en sammansatt resurs som en RunAs-användare. Om en sammansatt resurs anropar en annan sammansatta resurs, utförs även alla de resurserna som RunAs-användare. RunAs-autentiseringsuppgifterna har spridits till valfri nivå i hierarkin sammansatta resurs. Om en resurs inuti en sammansatt resurs anger värdet för **PsDscRunAsCredential**, en merge-fel resulterar under kompilering av konfiguration.

Det här exemplet visar användning med den [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) sammansatta resurser som ingår i modulen PSDesiredStateConfiguration.

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Att tillåta identiska duplicerade resurser i en konfiguration

DSC Tillåt inte och hantera motstridiga resursdefinitionerna i en konfiguration. Istället för att försöka lösa konflikten, helt enkelt misslyckas det. Eftersom konfigurationen återanvändning blir mer används via sammansatta resurser, inträffar etc. konflikter oftare. När motstridiga resursdefinitionerna är identiska, ska DSC vara smart och ge detta. Den här versionen har stöder vi att ha flera resursinstanser som har identiska definitioner:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

I tidigare versioner blir resultatet en misslyckad sammanställning på grund av en konflikt mellan WindowsFeature FE_IIS och WindowsFeature Worker_IIS instanser försöker se till att ”webbserver-rollen är installerad. Observera att *alla* egenskaper som konfigureras är identiska i dessa två konfigurationer. Eftersom *alla* egenskaper i dessa två resurser är identiska, detta resulterar i en lyckad sammanställning nu.

Om någon av egenskaperna skiljer sig mellan de två resurserna, anses inte vara identiska och kompilering misslyckas.

## <a name="dsc-module-and-configuration-signing-validations"></a>DSC-modulen och konfiguration signering verifieringar

I DSC distribueras konfigurationer och moduler till hanterade datorer från hämtningsservern. Om hämtningsservern komprometteras, kan en angripare potentiellt ändra konfigurationer och moduler på hämtningsservern och har den distribueras till alla hanterade noder.

I WMF 5.1 DSC stöder verifierar digitala signaturer på katalogen och konfiguration (. MOF) filer. Den här funktionen förhindrar att noder kör konfigurationer eller modulen filer som inte har signerats av en betrodd Signerare eller som någon har manipulerat när de har signerats av betrodda Signerare.

### <a name="how-to-sign-configuration-and-module"></a>Hur du registrerar konfiguration och modulen

- Konfigurationsfiler (. MOF-filer): Befintliga PowerShell-cmdleten [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) utökas för att stöda signering av MOF-filer.
- Moduler: Signering av moduler görs genom att registrera den motsvarande modul-katalog med följande steg:
  1. Skapa en katalogfil: En katalogfil innehåller en uppsättning kryptografiska hash-värden eller tumavtryck. Varje tumavtryck motsvarar en fil som ingår i modulen. Ny cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), har lagts till kan du skapa en katalogfil för sina modulen.
  2. Logga katalogfilen: Använd [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) logga katalogfilen.
  3. Placera katalogfilen inuti modulmappen som. Enligt konventionen används placeras katalogen modulfilen under modulmappen med samma namn som modulen.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>LocalConfigurationManager inställningar för att aktivera signering verifieringar

#### <a name="pull"></a>Hämta

LocalConfigurationManager för en nod utför signering validering av moduler och konfigurationer baserat på de aktuella inställningarna. Verifiera signaturen är inaktiverad som standard. Verifiera signaturen kan aktiveras genom att lägga till blockeringen 'SignatureValidation' definitionen meta-konfiguration för noden som visas nedan:

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

Inställningen ovan metaconfiguration på en nod kan verifiera signaturen på hämtade konfigurationer och moduler. Den lokala Konfigurationshanteraren utför följande steg för att verifiera de digitala signaturerna.

1. Verifiera signaturen på en konfigurationsfil (. MOF) är giltig med hjälp av den `Get-AuthenticodeSignature` cmdlet.
2. Kontrollera den certifikatutfärdare som auktoriserad undertecknarens är betrodd.
3. Hämta modulen/resursberoenden av konfigurationen till en tillfällig plats.
4. Verifiera signaturen på den katalog som ingår i modulen.
   - Hitta en `<moduleName>.cat` och kontrollera sin signatur med hjälp av `Get-AuthenticodeSignature`.
   - Kontrollera den certifikatutfärdare som autentiseras undertecknarens är betrodd.
   - Kontrollera innehållet i modulerna som inte har ändrats med hjälp av den nya cmdleten `Test-FileCatalog`.
5. `Install-Module` Att `$env:ProgramFiles\WindowsPowerShell\Modules\`
6. Processkonfiguration

> [!NOTE]
> Verifiera signaturen på modul-katalog och konfigurationen utförs endast när konfigurationen tillämpas i systemet för första gången eller när modulen hämtas och installeras.
> Konsekvenskontroll körs validerar inte signaturen för Current.mof eller dess modulberoenden. Om det gick inte att verifiera under alla stadier, exempelvis om konfigurationen som hämtats från hämtningsservern är osignerat, sedan bearbetningen av konfigurationen avslutas med fel som visas nedan och alla temporära filer tas bort.

![Exempelkonfiguration fel utdata](../images/PullUnsignedConfigFail.png)

På samma sätt kan signerat dra en modul vars katalogen inte är resulterar i följande fel:

![Exempelmodulen fel utdata](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

En konfiguration som levereras med hjälp av push kan vara har manipulerats vid dess källa innan det levereras till noden. Den lokala Konfigurationshanteraren utför liknande steg för verifiering av signaturen för pushade eller publicerade konfiguration(er). Nedan visas ett exempel på att verifiera signaturen för push-installation.

- Aktivera verifiera signaturen på noden.

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

- Skapa en exempel-konfigurationsfil.

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

- Försök skicka osignerade konfigurationsfilen till noden.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Logga konfigurationsfilen med hjälp av kodsigneringscertifikat.

  ![SignMofFile](../images/SignMofFile.png)

- Testa push-överför den signerade MOF-filen.

  ![SignMofFile](../images/PushSignedMof.png)
