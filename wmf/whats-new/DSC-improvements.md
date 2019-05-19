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
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="b87f1-103">Förbättringar i Desired State Configuration (DSC) i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b87f1-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="b87f1-104">Förbättringar av DSC-klass resurs</span><span class="sxs-lookup"><span data-stu-id="b87f1-104">DSC class resource improvements</span></span>

<span data-ttu-id="b87f1-105">Vi har åtgärdat följande kända problem i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="b87f1-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="b87f1-106">Get-DscConfiguration kan returnera tomma värden (null) eller om en komplex/hash-tabelltyp returneras av Get() funktion för en klassbaserade DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="b87f1-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="b87f1-107">Get-DscConfiguration returnerar fel om RunAs-autentiseringsuppgift används i DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b87f1-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="b87f1-108">MOF-baserade resursen kan inte användas i en sammansatt konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b87f1-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="b87f1-109">Start-DscConfiguration låser sig om MOF-baserade resurs har en egenskap för sin egen typ.</span><span class="sxs-lookup"><span data-stu-id="b87f1-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="b87f1-110">MOF-baserade resursen kan inte användas som en exklusiv resurs.</span><span class="sxs-lookup"><span data-stu-id="b87f1-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="b87f1-111">Felsökningsförbättringar för DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="b87f1-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="b87f1-112">I WMF 5.0 stoppades PowerShell-felsökare inte på klass-baserad resurs-metoden (Get/Set/Test) direkt.</span><span class="sxs-lookup"><span data-stu-id="b87f1-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="b87f1-113">I WMF 5.1 stoppar felsökningsprogrammet vid MOF-baserade resurs-metod på samma sätt som för MOF-baserade resurser metoder.</span><span class="sxs-lookup"><span data-stu-id="b87f1-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="b87f1-114">DSC pull-klienten har stöd för TLS 1.1 och TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="b87f1-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="b87f1-115">Tidigare stöds hämtningsklient DSC endast SSL3.0 och TLS 1.0 över HTTPS-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="b87f1-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="b87f1-116">När du tvungen att använda säkrare protokoll, skulle pull-klienten sluta fungera.</span><span class="sxs-lookup"><span data-stu-id="b87f1-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="b87f1-117">I WMF 5.1 DSC pull klienten inte längre har stöd för SSL 3.0 och lägger till stöd för protokollen säkrare TLS 1.1 och TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="b87f1-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="b87f1-118">Förbättrad pull-serverregistrering</span><span class="sxs-lookup"><span data-stu-id="b87f1-118">Improved pull server registration</span></span>

<span data-ttu-id="b87f1-119">I tidigare versioner av WMF skulle samtidiga registreringar/reporting begäranden till en DSC-hämtningsserver när du använder ESENT-databasen leda till LCM som inte kan registrera och/eller rapport.</span><span class="sxs-lookup"><span data-stu-id="b87f1-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="b87f1-120">I sådana fall kan händelseloggarna på hämtningsservern har felet ”instansnamnet används redan”.</span><span class="sxs-lookup"><span data-stu-id="b87f1-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="b87f1-121">Detta beror på ett felaktigt mönster som används för att få åtkomst till ESENT-databasen i ett scenario med flera trådar.</span><span class="sxs-lookup"><span data-stu-id="b87f1-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="b87f1-122">Det här problemet har åtgärdats i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="b87f1-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="b87f1-123">Samtidiga registreringar eller rapporter (som involverar ESENT-databas) fungerar bra i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="b87f1-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="b87f1-124">Det här problemet gäller endast för ESENT-databasen och gäller inte för OLEDB-databasen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="b87f1-125">Aktivera cirkulär inloggning ESENT-databasinstans</span><span class="sxs-lookup"><span data-stu-id="b87f1-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="b87f1-126">I eariler versioner av DSC-PullServer ESENT loggfiler fyller upp diskutrymme på den pullserver becouse databasinstansen som skapades utan cirkulär loggning.</span><span class="sxs-lookup"><span data-stu-id="b87f1-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="b87f1-127">I den här versionen har du möjlighet att styra den instansen med web.config i pullserver cirkulär loggning.</span><span class="sxs-lookup"><span data-stu-id="b87f1-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="b87f1-128">Som standard anges CircularLogging till TRUE.</span><span class="sxs-lookup"><span data-stu-id="b87f1-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="b87f1-129">WOW64-stöd för Konfigurationsnyckelord</span><span class="sxs-lookup"><span data-stu-id="b87f1-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="b87f1-130">Den `Configuration` nyckelordet stöds nu i WOW64 på en 64-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="b87f1-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="b87f1-131">Det innebär att en DSC-konfiguration kan definieras och kompileras i en 32-bitars process, till exempel Windows PowerShell ISE (x 86) som körs på en 64-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="b87f1-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="b87f1-132">Hämta namngivningskonvention för partiell konfiguration</span><span class="sxs-lookup"><span data-stu-id="b87f1-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="b87f1-133">I den föregående versionen Namngivningskonventionen för en partiell konfiguration var att MOF-filnamnet i pull-server/tjänsten måste matcha namnet partiell konfiguration i de lokala configuration manager-inställningar som i sin tur måste matcha den namn på inbäddade i MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="b87f1-134">Se ögonblicksbilder nedan:</span><span class="sxs-lookup"><span data-stu-id="b87f1-134">See the snapshots below:</span></span>

- <span data-ttu-id="b87f1-135">Lokala konfigurationsinställningar som definierar en partiell konfiguration som en nod kan ta emot.</span><span class="sxs-lookup"><span data-stu-id="b87f1-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Exemplet metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="b87f1-137">Partiell konfiguration exempeldefinition</span><span class="sxs-lookup"><span data-stu-id="b87f1-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="b87f1-138">{ConfigurationName} inbäddad i den genererade MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Exemplet genererade mof-filen](../images/PartialGeneratedMof.png)

- <span data-ttu-id="b87f1-140">Filnamn i pull-konfigurationsdatabasen</span><span class="sxs-lookup"><span data-stu-id="b87f1-140">FileName in the pull configuration repository</span></span>

  ![Filnamn i konfiguration av databas](../images/PartialInConfigRepository.png)

  <span data-ttu-id="b87f1-142">Azure Automation-tjänstnamn genereras MOF-filer som `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="b87f1-143">Av konfigurationen nedan kompilerar så att PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="b87f1-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="b87f1-144">Detta har gjort det omöjligt att pull en partiell konfigurationen från Azure Automation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="b87f1-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="b87f1-145">I WMF 5.1 kan en partiell konfiguration i pull-server/tjänsten namnges som `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="b87f1-146">Om en dator är att hämta en enda konfiguration från en pull ha/servertjänsten sedan konfigurationsfilen på konfigurationsdatabasen för pull-server dessutom valfritt filnamn.</span><span class="sxs-lookup"><span data-stu-id="b87f1-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="b87f1-147">Den här namngivning flexibiliteten kan du hantera dina noder delvis av Azure Automation-tjänsten var konfiguration till noden kommer från Azure Automation DSC och med en partiell konfiguration som du hanterar lokalt.</span><span class="sxs-lookup"><span data-stu-id="b87f1-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="b87f1-148">Metaconfiguration nedan ställer in en nod ska hanteras både lokalt samt av Azure Automation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="b87f1-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="b87f1-149">Med hjälp av PsDscRunAsCredential med DSC sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="b87f1-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="b87f1-150">Vi har lagt till stöd för användning av [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) med DSC [sammansatta](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resurser.</span><span class="sxs-lookup"><span data-stu-id="b87f1-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="b87f1-151">Du kan nu ange ett värde för **PsDscRunAsCredential** när du använder sammansatta resurser inuti konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b87f1-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="b87f1-152">När du anger körs alla resurser i en sammansatt resurs som en RunAs-användare.</span><span class="sxs-lookup"><span data-stu-id="b87f1-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="b87f1-153">Om en sammansatt resurs anropar en annan sammansatta resurs, utförs även alla de resurserna som RunAs-användare.</span><span class="sxs-lookup"><span data-stu-id="b87f1-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="b87f1-154">RunAs-autentiseringsuppgifterna har spridits till valfri nivå i hierarkin sammansatta resurs.</span><span class="sxs-lookup"><span data-stu-id="b87f1-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="b87f1-155">Om en resurs inuti en sammansatt resurs anger värdet för **PsDscRunAsCredential**, en merge-fel resulterar under kompilering av konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b87f1-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="b87f1-156">Det här exemplet visar användning med den [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) sammansatta resurser som ingår i modulen PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="b87f1-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="b87f1-157">Att tillåta identiska duplicerade resurser i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="b87f1-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="b87f1-158">DSC Tillåt inte och hantera motstridiga resursdefinitionerna i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b87f1-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="b87f1-159">Istället för att försöka lösa konflikten, helt enkelt misslyckas det.</span><span class="sxs-lookup"><span data-stu-id="b87f1-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="b87f1-160">Eftersom konfigurationen återanvändning blir mer används via sammansatta resurser, inträffar etc. konflikter oftare.</span><span class="sxs-lookup"><span data-stu-id="b87f1-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="b87f1-161">När motstridiga resursdefinitionerna är identiska, ska DSC vara smart och ge detta.</span><span class="sxs-lookup"><span data-stu-id="b87f1-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="b87f1-162">Den här versionen har stöder vi att ha flera resursinstanser som har identiska definitioner:</span><span class="sxs-lookup"><span data-stu-id="b87f1-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="b87f1-163">I tidigare versioner blir resultatet en misslyckad sammanställning på grund av en konflikt mellan WindowsFeature FE_IIS och WindowsFeature Worker_IIS instanser försöker se till att ”webbserver-rollen är installerad.</span><span class="sxs-lookup"><span data-stu-id="b87f1-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="b87f1-164">Observera att *alla* egenskaper som konfigureras är identiska i dessa två konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b87f1-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="b87f1-165">Eftersom *alla* egenskaper i dessa två resurser är identiska, detta resulterar i en lyckad sammanställning nu.</span><span class="sxs-lookup"><span data-stu-id="b87f1-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="b87f1-166">Om någon av egenskaperna skiljer sig mellan de två resurserna, anses inte vara identiska och kompilering misslyckas.</span><span class="sxs-lookup"><span data-stu-id="b87f1-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="b87f1-167">DSC-modulen och konfiguration signering verifieringar</span><span class="sxs-lookup"><span data-stu-id="b87f1-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="b87f1-168">I DSC distribueras konfigurationer och moduler till hanterade datorer från hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="b87f1-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="b87f1-169">Om hämtningsservern komprometteras, kan en angripare potentiellt ändra konfigurationer och moduler på hämtningsservern och har den distribueras till alla hanterade noder.</span><span class="sxs-lookup"><span data-stu-id="b87f1-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="b87f1-170">I WMF 5.1 DSC stöder verifierar digitala signaturer på katalogen och konfiguration (. MOF) filer.</span><span class="sxs-lookup"><span data-stu-id="b87f1-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="b87f1-171">Den här funktionen förhindrar att noder kör konfigurationer eller modulen filer som inte har signerats av en betrodd Signerare eller som någon har manipulerat när de har signerats av betrodda Signerare.</span><span class="sxs-lookup"><span data-stu-id="b87f1-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="b87f1-172">Hur du registrerar konfiguration och modulen</span><span class="sxs-lookup"><span data-stu-id="b87f1-172">How to sign configuration and module</span></span>

- <span data-ttu-id="b87f1-173">Konfigurationsfiler (. MOF-filer): Befintliga PowerShell-cmdleten [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) utökas för att stöda signering av MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="b87f1-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="b87f1-174">Moduler: Signering av moduler görs genom att registrera den motsvarande modul-katalog med följande steg:</span><span class="sxs-lookup"><span data-stu-id="b87f1-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="b87f1-175">Skapa en katalogfil: En katalogfil innehåller en uppsättning kryptografiska hash-värden eller tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="b87f1-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="b87f1-176">Varje tumavtryck motsvarar en fil som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="b87f1-177">Ny cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), har lagts till kan du skapa en katalogfil för sina modulen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="b87f1-178">Logga katalogfilen: Använd [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) logga katalogfilen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="b87f1-179">Placera katalogfilen inuti modulmappen som.</span><span class="sxs-lookup"><span data-stu-id="b87f1-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="b87f1-180">Enligt konventionen används placeras katalogen modulfilen under modulmappen med samma namn som modulen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="b87f1-181">LocalConfigurationManager inställningar för att aktivera signering verifieringar</span><span class="sxs-lookup"><span data-stu-id="b87f1-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="b87f1-182">Hämta</span><span class="sxs-lookup"><span data-stu-id="b87f1-182">Pull</span></span>

<span data-ttu-id="b87f1-183">LocalConfigurationManager för en nod utför signering validering av moduler och konfigurationer baserat på de aktuella inställningarna.</span><span class="sxs-lookup"><span data-stu-id="b87f1-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="b87f1-184">Verifiera signaturen är inaktiverad som standard.</span><span class="sxs-lookup"><span data-stu-id="b87f1-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="b87f1-185">Verifiera signaturen kan aktiveras genom att lägga till blockeringen 'SignatureValidation' definitionen meta-konfiguration för noden som visas nedan:</span><span class="sxs-lookup"><span data-stu-id="b87f1-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="b87f1-186">Inställningen ovan metaconfiguration på en nod kan verifiera signaturen på hämtade konfigurationer och moduler.</span><span class="sxs-lookup"><span data-stu-id="b87f1-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="b87f1-187">Den lokala Konfigurationshanteraren utför följande steg för att verifiera de digitala signaturerna.</span><span class="sxs-lookup"><span data-stu-id="b87f1-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="b87f1-188">Verifiera signaturen på en konfigurationsfil (. MOF) är giltig med hjälp av den `Get-AuthenticodeSignature` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b87f1-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="b87f1-189">Kontrollera den certifikatutfärdare som auktoriserad undertecknarens är betrodd.</span><span class="sxs-lookup"><span data-stu-id="b87f1-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="b87f1-190">Hämta modulen/resursberoenden av konfigurationen till en tillfällig plats.</span><span class="sxs-lookup"><span data-stu-id="b87f1-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="b87f1-191">Verifiera signaturen på den katalog som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="b87f1-192">Hitta en `<moduleName>.cat` och kontrollera sin signatur med hjälp av `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="b87f1-193">Kontrollera den certifikatutfärdare som autentiseras undertecknarens är betrodd.</span><span class="sxs-lookup"><span data-stu-id="b87f1-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="b87f1-194">Kontrollera innehållet i modulerna som inte har ändrats med hjälp av den nya cmdleten `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="b87f1-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="b87f1-195">`Install-Module` Att `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="b87f1-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="b87f1-196">Processkonfiguration</span><span class="sxs-lookup"><span data-stu-id="b87f1-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="b87f1-197">Verifiera signaturen på modul-katalog och konfigurationen utförs endast när konfigurationen tillämpas i systemet för första gången eller när modulen hämtas och installeras.</span><span class="sxs-lookup"><span data-stu-id="b87f1-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="b87f1-198">Konsekvenskontroll körs validerar inte signaturen för Current.mof eller dess modulberoenden.</span><span class="sxs-lookup"><span data-stu-id="b87f1-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="b87f1-199">Om det gick inte att verifiera under alla stadier, exempelvis om konfigurationen som hämtats från hämtningsservern är osignerat, sedan bearbetningen av konfigurationen avslutas med fel som visas nedan och alla temporära filer tas bort.</span><span class="sxs-lookup"><span data-stu-id="b87f1-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exempelkonfiguration fel utdata](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="b87f1-201">På samma sätt kan signerat dra en modul vars katalogen inte är resulterar i följande fel:</span><span class="sxs-lookup"><span data-stu-id="b87f1-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Exempelmodulen fel utdata](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="b87f1-203">Push</span><span class="sxs-lookup"><span data-stu-id="b87f1-203">Push</span></span>

<span data-ttu-id="b87f1-204">En konfiguration som levereras med hjälp av push kan vara har manipulerats vid dess källa innan det levereras till noden.</span><span class="sxs-lookup"><span data-stu-id="b87f1-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="b87f1-205">Den lokala Konfigurationshanteraren utför liknande steg för verifiering av signaturen för pushade eller publicerade konfiguration(er).</span><span class="sxs-lookup"><span data-stu-id="b87f1-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="b87f1-206">Nedan visas ett exempel på att verifiera signaturen för push-installation.</span><span class="sxs-lookup"><span data-stu-id="b87f1-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="b87f1-207">Aktivera verifiera signaturen på noden.</span><span class="sxs-lookup"><span data-stu-id="b87f1-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="b87f1-208">Skapa en exempel-konfigurationsfil.</span><span class="sxs-lookup"><span data-stu-id="b87f1-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="b87f1-209">Försök skicka osignerade konfigurationsfilen till noden.</span><span class="sxs-lookup"><span data-stu-id="b87f1-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="b87f1-211">Logga konfigurationsfilen med hjälp av kodsigneringscertifikat.</span><span class="sxs-lookup"><span data-stu-id="b87f1-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="b87f1-213">Testa push-överför den signerade MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="b87f1-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/PushSignedMof.png)
