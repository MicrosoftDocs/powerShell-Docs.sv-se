---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: DSC-förbättringar i WMF 5.1
ms.openlocfilehash: 445d0f7bb54c6b21b6af26c4174f3d6422caf6dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771557"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Förbättringar i önskad tillstånds konfiguration (DSC) i WMF 5,1

## <a name="dsc-class-resource-improvements"></a>Förbättringar av DSC-klass resurser

I WMF 5,1 har vi åtgärdat följande kända problem:

- Get-DscConfiguration kan returnera tomma värden (null) eller fel om en komplex/hash-tabell typ returneras av Get ()-funktionen för en klassbaserade DSC-resurs.
- Get-DscConfiguration returnerar fel om RunAs-autentiseringsuppgiften används i DSC-konfigurationen.
- Det går inte att använda klassbaserade resurser i en sammansatt konfiguration.
- Start-DscConfiguration låser sig om klassbaserade resurser har en egenskap av en egen typ.
- Det går inte att använda klassbaserade resurser som en exklusiv resurs.

## <a name="dsc-resource-debugging-improvements"></a>Förbättringar av DSC-felsökning

I WMF 5,0 stoppades inte PowerShell-felsökning vid den klassbaserade resurs metoden (Hämta/ange/testa) direkt. I WMF 5,1 stoppar fel söknings programmet vid den klassbaserade resurs metoden på samma sätt som för MOF-baserade resurs metoder.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC pull-klienten har stöd för TLS 1,1 och TLS 1,2

Tidigare stöddes endast SSL 3.0 och TLS 1.0 över HTTPS-pull-klienten. När du tvingas använda fler säkra protokoll slutar pull-klienten att fungera. I WMF 5,1 stöder DSC-pull-klienten inte längre SSL 3,0 och lägger till stöd för de säkrare TLS 1,1-och TLS 1,2-protokollen.

## <a name="improved-pull-server-registration"></a>Förbättrad registrering av hämtnings servrar

I tidigare versioner av WMF skulle samtidiga registreringar/rapporterings begär anden till en DSC-pull-server när du använder ESENT-databasen leda till att LCM inte kan registreras och/eller rapporteras. I sådana fall har händelse loggarna på hämtnings servern fel "instans namnet används redan". Detta orsakades av ett felaktigt mönster som användes för att komma åt ESENT-databasen i ett scenario med flera trådar. Det här problemet har åtgärd ATS i WMF 5,1. Samtidiga registreringar eller rapportering (som inbegriper ESENT-databasen) fungerar bra i WMF 5,1. Det här problemet gäller endast för ESENT-databasen och gäller inte för OLEDB-databasen.

## <a name="enable-circular-log-on-esent-database-instance"></a>Aktivera cirkulär inloggning på en ESENT-databas instans

I eariler-versionen av DSC-PullServer, fyller ESENT-databasens loggfiler upp disk utrymmet för PullServer eftersom databas instansen skapades utan cirkulär loggning. I den här versionen har du möjlighet att styra det cirkulära loggnings beteendet för instansen med hjälp av web.config i pullserver. Som standard har CircularLogging angetts till TRUE.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>WOW64-stöd för konfigurations nyckelord

`Configuration`Nyckelordet stöds nu i WOW64 på en 64-bitars dator. Det innebär att en DSC-konfiguration kan definieras och kompileras i en 32-bitars process som Windows PowerShell ISE (x86) som körs på en 64-bitars dator.

## <a name="pull-partial-configuration-naming-convention"></a>Hämta partiell konfiguration namngivnings konvention

I den tidigare versionen var namngivnings konventionen för en partiell konfiguration att MOF-filnamnet i pull-servern/tjänsten ska matcha det partiella konfigurations namn som anges i den lokala Configuration Manager-inställningarna som i sin tur måste matcha konfigurations namnet som är inbäddat i MOF-filen.

Se ögonblicks bilderna nedan:

- Lokala konfigurations inställningar som definierar en delvis konfiguration som en nod får ta emot.

  ![Exempel på metaconfiguration](media/DSC-improvements/MetaConfigPartialOne.png)

- Exempel på partiell konfigurations definition

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

- ' ConfigurationName ' Embedded i den genererade MOF-filen.

  ![Exempel på genererad MOF-fil](media/DSC-improvements/PartialGeneratedMof.png)

- Fil namn i hämtnings konfigurationens lagrings plats

  ![Fil namn i konfigurations lager](media/DSC-improvements/PartialInConfigRepository.png)

  Azure Automation tjänst namn genererade MOF-filer som `<ConfigurationName>.<NodeName>.mof` . Konfigurationen nedan kompileras till PartialOne. localhost. mof.

  Detta gjorde det omöjligt att hämta en delvis konfiguration från Azure Automation-tjänsten.

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

  I WMF 5,1 kan en del konfiguration i pull-servern/-tjänsten namnges som `<ConfigurationName>.<NodeName>.mof` . Dessutom, om en dator hämtar en enda konfiguration från en pull-server/tjänst, kan konfigurations filen på lagrings serverns konfigurations lagring ha alla fil namn. Den här namn flexibiliteten gör att du kan hantera dina noder delvis av Azure Automation tjänst, där viss konfiguration för noden kommer från Azure Automation DSC och med en delvis konfiguration som du hanterar lokalt.

  Metaconfiguration nedan ställer in en nod som ska hanteras både lokalt och per Azure Automation tjänst.

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Använda PsDscRunAsCredential med sammansatta DSC-resurser

Vi har lagt till stöd för att använda [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) med [SAMMANsatta](/powershell/scripting/dsc/resources/authoringresourcecomposite) DSC-resurser.

Nu kan du ange ett värde för **PsDscRunAsCredential** när du använder sammansatta resurser i konfigurationer. När det här anges körs alla resurser i en sammansatt resurs som en RunAs-användare. Om en sammansatt resurs anropar en annan sammansatt resurs körs alla dessa resurser också som RunAs-användare. RunAs-autentiseringsuppgifter sprids till valfri nivå i den sammansatta resursens hierarki. Om en resurs i en sammansatt resurs anger sitt eget värde för **PsDscRunAsCredential**uppstår ett sammanfognings fel vid konfigurations kompilering.

Det här exemplet visar användningen med den sammansatta [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) -resursen som ingår i PSDesiredStateConfiguration-modulen.

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Tillåta identiska duplicerade resurser i en konfiguration

DSC tillåter eller hanterar inte resurs definitioner som är i konflikt med varandra i en konfiguration. I stället för att försöka lösa konflikten fungerar det bara. När återanvändning av konfigurationen blir mer utnyttjad via sammansatta resurser, så inträffar konflikter oftare. När resurs definitionerna i konflikt är identiska bör DSC vara smart och tillåta detta. I den här versionen stöder vi flera resurs instanser som har identiska definitioner:

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

I tidigare versioner skulle resultatet bli en misslyckad kompilering på grund av en konflikt mellan FE_IIS-och WindowsFeature-Worker_IIS instanser som försöker se till att rollen webb server är installerad. Observera att *alla* egenskaper som konfigureras är identiska i de här två konfigurationerna. Eftersom *alla* egenskaper i de här två resurserna är identiska, leder det till en lyckad kompilering nu.

Om någon av egenskaperna skiljer sig mellan de två resurserna kommer de inte att anses vara identiska och kompileringen kommer inte att fungera.

## <a name="dsc-module-and-configuration-signing-validations"></a>Validering av DSC-modul och konfigurations signering

I DSC distribueras konfigurationer och moduler till hanterade datorer från pull-servern. Om hämtnings servern komprometteras kan en angripare ändra konfigurationerna och modulerna på pull-servern och distribuera dem till alla hanterade noder.

I WMF 5,1 stöder DSC validering av de digitala signaturerna i katalogen och konfigurationen (. MOF-filer. Den här funktionen förhindrar att noder kör konfigurationer eller modulblad som inte har signerats av en betrodd undertecknare eller som har ändrats efter att de har signerats av en betrodd undertecknare.

### <a name="how-to-sign-configuration-and-module"></a>Så här signerar du konfiguration och modul

- Konfigurationsfiler (. MOF: ar): den befintliga PowerShell-cmdleten [set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) har utökats för att stödja signering av MOF-filer.
- Moduler: signering av moduler görs genom att du signerar motsvarande modul katalog med hjälp av följande steg:
  1. Skapa en katalog fil: en katalog fil innehåller en samling kryptografiska hash-värden eller tumavtrycken. Varje tumavtryck motsvarar en fil som ingår i modulen. Den nya cmdleten [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog)har lagts till för att göra det möjligt för användare att skapa en katalog fil för sin modul.
  2. Signera katalog filen: Använd [set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) för att signera katalog filen.
  3. Placera katalog filen i mappen modul. Per konvention bör modulens katalog fil placeras under mappen module med samma namn som modulen.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>LocalConfigurationManager-inställningar för att aktivera signerings valideringar

#### <a name="pull"></a>Pull

LocalConfigurationManager för en nod utför signerings valideringen av moduler och konfigurationer baserat på dess aktuella inställningar. Som standard är verifiering av signaturer inaktiverat. Verifiering av signaturen kan aktive ras genom att SignatureValidation-blocket läggs till i definitionen av meta-konfigurationen för noden enligt nedan:

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

Genom att ställa in ovanstående metaconfiguration på en nod kan du verifiera signaturen på nedladdade konfigurationer och moduler. Den lokala Configuration Manager utför följande steg för att verifiera de digitala signaturerna.

1. Verifiera signaturen för en konfigurations fil (. MOF) är giltig med `Get-AuthenticodeSignature` cmdleten.
2. Verifiera den certifikat utfärdare som har behörighet att signeraren är betrodd.
3. Hämta modul/resurs beroenden för konfigurationen till en tillfällig plats.
4. Kontrol lera signaturen för katalogen som ingår i modulen.
   - Hitta en `<moduleName>.cat` fil och verifiera signaturen med hjälp av `Get-AuthenticodeSignature` .
   - Verifiera att den certifikat utfärdare som autentiserat signeraren är betrodd.
   - Kontrol lera att innehållet i modulerna inte har ändrats med den nya cmdleten `Test-FileCatalog` .
5. `Install-Module` att `$env:ProgramFiles\WindowsPowerShell\Modules\`
6. Process konfiguration

> [!NOTE]
> Verifiering av signaturen för modul-katalog och konfiguration utförs bara när konfigurationen tillämpas på systemet för första gången eller när modulen laddas ned och installeras.
> Konsekvens körningar verifierar inte signaturen för current. MOF eller dess beroenden. Om verifieringen Miss lyckas i något skede, till exempel om konfigurationen som hämtades från hämtnings servern är osignerad, avslutas bearbetningen av konfigurationen med det fel som visas nedan och alla temporära filer tas bort.

![Exempel på utdata-konfiguration](media/DSC-improvements/PullUnsignedConfigFail.png)

På samma sätt kan du hämta en modul vars katalog inte är signerade resultat i följande fel:

![Exempel på utdata-modul](media/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

En konfiguration som levereras med push-teknik kan manipuleras på källan innan den skickas till noden. Den lokala Configuration Manager utför liknande validerings steg för signaturer för push-eller publicerad konfiguration (er). Nedan visas ett fullständigt exempel på verifiering av signaturen för push.

- Aktivera verifiering av signatur på noden.

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

- Skapa en exempel konfigurations fil.

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

- Försök att skicka den osignerade konfigurations filen till noden.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![Fel-osignerad MOF-fil har överförts](media/DSC-improvements/PushUnsignedMof.png)

- Signera konfigurations filen med kod signerings certifikat.

  ![Signera MOF-filen](media/DSC-improvements/SignMofFile.png)

- Försök att skicka den signerade MOF-filen.

  ![Skicka den signerade MOF-filen](media/DSC-improvements/PushSignedMof.png)
