---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: DSC-förbättringar i WMF 5.1
ms.openlocfilehash: 78c15f453977384ba437b0bd69cd620eb1a29fbd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978295"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="2cde0-103">Förbättringar i önskad tillstånds konfiguration (DSC) i WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="2cde0-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="2cde0-104">Förbättringar av DSC-klass resurser</span><span class="sxs-lookup"><span data-stu-id="2cde0-104">DSC class resource improvements</span></span>

<span data-ttu-id="2cde0-105">I WMF 5,1 har vi åtgärdat följande kända problem:</span><span class="sxs-lookup"><span data-stu-id="2cde0-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="2cde0-106">Get-DscConfiguration kan returnera tomma värden (null) eller fel om en komplex/hash-tabell typ returneras av Get ()-funktionen för en klassbaserade DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="2cde0-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="2cde0-107">Get-DscConfiguration returnerar fel om RunAs-autentiseringsuppgiften används i DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="2cde0-108">Det går inte att använda klassbaserade resurser i en sammansatt konfiguration.</span><span class="sxs-lookup"><span data-stu-id="2cde0-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="2cde0-109">Start-DscConfiguration låser sig om klassbaserade resurser har en egenskap av en egen typ.</span><span class="sxs-lookup"><span data-stu-id="2cde0-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="2cde0-110">Det går inte att använda klassbaserade resurser som en exklusiv resurs.</span><span class="sxs-lookup"><span data-stu-id="2cde0-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="2cde0-111">Förbättringar av DSC-felsökning</span><span class="sxs-lookup"><span data-stu-id="2cde0-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="2cde0-112">I WMF 5,0 stoppades inte PowerShell-felsökning vid den klassbaserade resurs metoden (Hämta/ange/testa) direkt.</span><span class="sxs-lookup"><span data-stu-id="2cde0-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="2cde0-113">I WMF 5,1 stoppar fel söknings programmet vid den klassbaserade resurs metoden på samma sätt som för MOF-baserade resurs metoder.</span><span class="sxs-lookup"><span data-stu-id="2cde0-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="2cde0-114">DSC pull-klienten har stöd för TLS 1,1 och TLS 1,2</span><span class="sxs-lookup"><span data-stu-id="2cde0-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="2cde0-115">Tidigare stöddes endast SSL 3.0 och TLS 1.0 över HTTPS-pull-klienten.</span><span class="sxs-lookup"><span data-stu-id="2cde0-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="2cde0-116">När du tvingas använda fler säkra protokoll slutar pull-klienten att fungera.</span><span class="sxs-lookup"><span data-stu-id="2cde0-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="2cde0-117">I WMF 5,1 stöder DSC-pull-klienten inte längre SSL 3,0 och lägger till stöd för de säkrare TLS 1,1-och TLS 1,2-protokollen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="2cde0-118">Förbättrad registrering av hämtnings servrar</span><span class="sxs-lookup"><span data-stu-id="2cde0-118">Improved pull server registration</span></span>

<span data-ttu-id="2cde0-119">I tidigare versioner av WMF skulle samtidiga registreringar/rapporterings begär anden till en DSC-pull-server när du använder ESENT-databasen leda till att LCM inte kan registreras och/eller rapporteras.</span><span class="sxs-lookup"><span data-stu-id="2cde0-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="2cde0-120">I sådana fall har händelse loggarna på hämtnings servern fel "instans namnet används redan".</span><span class="sxs-lookup"><span data-stu-id="2cde0-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="2cde0-121">Detta orsakades av ett felaktigt mönster som användes för att komma åt ESENT-databasen i ett scenario med flera trådar.</span><span class="sxs-lookup"><span data-stu-id="2cde0-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="2cde0-122">Det här problemet har åtgärd ATS i WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="2cde0-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="2cde0-123">Samtidiga registreringar eller rapportering (som inbegriper ESENT-databasen) fungerar bra i WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="2cde0-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="2cde0-124">Det här problemet gäller endast för ESENT-databasen och gäller inte för OLEDB-databasen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="2cde0-125">Aktivera cirkulär inloggning på en ESENT-databas instans</span><span class="sxs-lookup"><span data-stu-id="2cde0-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="2cde0-126">I eariler-versionen av DSC-PullServer, fyller ESENT-databasens loggfiler upp disk utrymmet för PullServer eftersom databas instansen skapades utan cirkulär loggning.</span><span class="sxs-lookup"><span data-stu-id="2cde0-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver because the database instance was being created without circular logging.</span></span> <span data-ttu-id="2cde0-127">I den här versionen har du möjlighet att styra det cirkulära loggnings beteendet för instansen med hjälp av Web. config för pullserver.</span><span class="sxs-lookup"><span data-stu-id="2cde0-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="2cde0-128">Som standard har CircularLogging angetts till TRUE.</span><span class="sxs-lookup"><span data-stu-id="2cde0-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="2cde0-129">WOW64-stöd för konfigurations nyckelord</span><span class="sxs-lookup"><span data-stu-id="2cde0-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="2cde0-130">`Configuration` Nyckelordet stöds nu i WOW64 på en 64-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="2cde0-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="2cde0-131">Det innebär att en DSC-konfiguration kan definieras och kompileras i en 32-bitars process som Windows PowerShell ISE (x86) som körs på en 64-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="2cde0-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="2cde0-132">Hämta partiell konfiguration namngivnings konvention</span><span class="sxs-lookup"><span data-stu-id="2cde0-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="2cde0-133">I den tidigare versionen var namngivnings konventionen för en partiell konfiguration att MOF-filnamnet i pull-servern/tjänsten ska matcha det partiella konfigurations namn som anges i den lokala Configuration Manager-inställningarna som i sin tur måste matcha konfigurations namnet som är inbäddat i MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="2cde0-134">Se ögonblicks bilderna nedan:</span><span class="sxs-lookup"><span data-stu-id="2cde0-134">See the snapshots below:</span></span>

- <span data-ttu-id="2cde0-135">Lokala konfigurations inställningar som definierar en delvis konfiguration som en nod får ta emot.</span><span class="sxs-lookup"><span data-stu-id="2cde0-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Exempel på metaconfiguration](media/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="2cde0-137">Exempel på partiell konfigurations definition</span><span class="sxs-lookup"><span data-stu-id="2cde0-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="2cde0-138">' ConfigurationName ' Embedded i den genererade MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Exempel på genererad MOF-fil](media/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="2cde0-140">Fil namn i hämtnings konfigurationens lagrings plats</span><span class="sxs-lookup"><span data-stu-id="2cde0-140">FileName in the pull configuration repository</span></span>

  ![Fil namn i konfigurations lager](media/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="2cde0-142">Azure Automation tjänst namn genererade MOF- `<ConfigurationName>.<NodeName>.mof`filer som.</span><span class="sxs-lookup"><span data-stu-id="2cde0-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="2cde0-143">Konfigurationen nedan kompileras till PartialOne. localhost. mof.</span><span class="sxs-lookup"><span data-stu-id="2cde0-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="2cde0-144">Detta gjorde det omöjligt att hämta en delvis konfiguration från Azure Automation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="2cde0-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="2cde0-145">I WMF 5,1 kan en del konfiguration i pull-servern/-tjänsten namnges som `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="2cde0-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="2cde0-146">Dessutom, om en dator hämtar en enda konfiguration från en pull-server/tjänst, kan konfigurations filen på lagrings serverns konfigurations lagring ha alla fil namn.</span><span class="sxs-lookup"><span data-stu-id="2cde0-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="2cde0-147">Den här namn flexibiliteten gör att du kan hantera dina noder delvis av Azure Automation tjänst, där viss konfiguration för noden kommer från Azure Automation DSC och med en delvis konfiguration som du hanterar lokalt.</span><span class="sxs-lookup"><span data-stu-id="2cde0-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="2cde0-148">Metaconfiguration nedan ställer in en nod som ska hanteras både lokalt och per Azure Automation tjänst.</span><span class="sxs-lookup"><span data-stu-id="2cde0-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="2cde0-149">Använda PsDscRunAsCredential med sammansatta DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="2cde0-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="2cde0-150">Vi har lagt till stöd för att använda [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) med [SAMMANsatta](/powershell/scripting/dsc/resources/authoringresourcecomposite) DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="2cde0-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/resources/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="2cde0-151">Nu kan du ange ett värde för **PsDscRunAsCredential** när du använder sammansatta resurser i konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="2cde0-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="2cde0-152">När det här anges körs alla resurser i en sammansatt resurs som en RunAs-användare.</span><span class="sxs-lookup"><span data-stu-id="2cde0-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="2cde0-153">Om en sammansatt resurs anropar en annan sammansatt resurs körs alla dessa resurser också som RunAs-användare.</span><span class="sxs-lookup"><span data-stu-id="2cde0-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="2cde0-154">RunAs-autentiseringsuppgifter sprids till valfri nivå i den sammansatta resursens hierarki.</span><span class="sxs-lookup"><span data-stu-id="2cde0-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="2cde0-155">Om en resurs i en sammansatt resurs anger sitt eget värde för **PsDscRunAsCredential**uppstår ett sammanfognings fel vid konfigurations kompilering.</span><span class="sxs-lookup"><span data-stu-id="2cde0-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="2cde0-156">Det här exemplet visar användningen med den sammansatta [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) -resursen som ingår i PSDesiredStateConfiguration-modulen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="2cde0-157">Tillåta identiska duplicerade resurser i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="2cde0-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="2cde0-158">DSC tillåter eller hanterar inte resurs definitioner som är i konflikt med varandra i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="2cde0-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="2cde0-159">I stället för att försöka lösa konflikten fungerar det bara.</span><span class="sxs-lookup"><span data-stu-id="2cde0-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="2cde0-160">När återanvändning av konfigurationen blir mer utnyttjad via sammansatta resurser, så inträffar konflikter oftare.</span><span class="sxs-lookup"><span data-stu-id="2cde0-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="2cde0-161">När resurs definitionerna i konflikt är identiska bör DSC vara smart och tillåta detta.</span><span class="sxs-lookup"><span data-stu-id="2cde0-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="2cde0-162">I den här versionen stöder vi flera resurs instanser som har identiska definitioner:</span><span class="sxs-lookup"><span data-stu-id="2cde0-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="2cde0-163">I tidigare versioner skulle resultatet bli en misslyckad kompilering på grund av en konflikt mellan FE_IIS-och WindowsFeature-Worker_IIS instanser som försöker se till att rollen webb server är installerad.</span><span class="sxs-lookup"><span data-stu-id="2cde0-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="2cde0-164">Observera att *alla* egenskaper som konfigureras är identiska i de här två konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="2cde0-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="2cde0-165">Eftersom *alla* egenskaper i de här två resurserna är identiska, leder det till en lyckad kompilering nu.</span><span class="sxs-lookup"><span data-stu-id="2cde0-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="2cde0-166">Om någon av egenskaperna skiljer sig mellan de två resurserna kommer de inte att anses vara identiska och kompileringen kommer inte att fungera.</span><span class="sxs-lookup"><span data-stu-id="2cde0-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="2cde0-167">Validering av DSC-modul och konfigurations signering</span><span class="sxs-lookup"><span data-stu-id="2cde0-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="2cde0-168">I DSC distribueras konfigurationer och moduler till hanterade datorer från pull-servern.</span><span class="sxs-lookup"><span data-stu-id="2cde0-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="2cde0-169">Om hämtnings servern komprometteras kan en angripare ändra konfigurationerna och modulerna på pull-servern och distribuera dem till alla hanterade noder.</span><span class="sxs-lookup"><span data-stu-id="2cde0-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="2cde0-170">I WMF 5,1 stöder DSC validering av de digitala signaturerna i katalogen och konfigurationen (. MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="2cde0-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="2cde0-171">Den här funktionen förhindrar att noder kör konfigurationer eller modulblad som inte har signerats av en betrodd undertecknare eller som har ändrats efter att de har signerats av en betrodd undertecknare.</span><span class="sxs-lookup"><span data-stu-id="2cde0-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="2cde0-172">Så här signerar du konfiguration och modul</span><span class="sxs-lookup"><span data-stu-id="2cde0-172">How to sign configuration and module</span></span>

- <span data-ttu-id="2cde0-173">Konfigurationsfiler (. MOF: ar): den befintliga PowerShell-cmdleten [set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) har utökats för att stödja signering av MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="2cde0-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="2cde0-174">Moduler: signering av moduler görs genom att du signerar motsvarande modul katalog med hjälp av följande steg:</span><span class="sxs-lookup"><span data-stu-id="2cde0-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="2cde0-175">Skapa en katalog fil: en katalog fil innehåller en samling kryptografiska hash-värden eller tumavtrycken.</span><span class="sxs-lookup"><span data-stu-id="2cde0-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="2cde0-176">Varje tumavtryck motsvarar en fil som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="2cde0-177">Den nya cmdleten [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog)har lagts till för att göra det möjligt för användare att skapa en katalog fil för sin modul.</span><span class="sxs-lookup"><span data-stu-id="2cde0-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="2cde0-178">Signera katalog filen: Använd [set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) för att signera katalog filen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="2cde0-179">Placera katalog filen i mappen modul.</span><span class="sxs-lookup"><span data-stu-id="2cde0-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="2cde0-180">Per konvention bör modulens katalog fil placeras under mappen module med samma namn som modulen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="2cde0-181">LocalConfigurationManager-inställningar för att aktivera signerings valideringar</span><span class="sxs-lookup"><span data-stu-id="2cde0-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="2cde0-182">Pull</span><span class="sxs-lookup"><span data-stu-id="2cde0-182">Pull</span></span>

<span data-ttu-id="2cde0-183">LocalConfigurationManager för en nod utför signerings valideringen av moduler och konfigurationer baserat på dess aktuella inställningar.</span><span class="sxs-lookup"><span data-stu-id="2cde0-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="2cde0-184">Som standard är verifiering av signaturer inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="2cde0-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="2cde0-185">Verifiering av signaturen kan aktive ras genom att SignatureValidation-blocket läggs till i definitionen av meta-konfigurationen för noden enligt nedan:</span><span class="sxs-lookup"><span data-stu-id="2cde0-185">Signature validation can enabled by adding the 'SignatureValidation' block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="2cde0-186">Genom att ställa in ovanstående metaconfiguration på en nod kan du verifiera signaturen på nedladdade konfigurationer och moduler.</span><span class="sxs-lookup"><span data-stu-id="2cde0-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="2cde0-187">Den lokala Configuration Manager utför följande steg för att verifiera de digitala signaturerna.</span><span class="sxs-lookup"><span data-stu-id="2cde0-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="2cde0-188">Verifiera signaturen för en konfigurations fil (. MOF) är giltig med `Get-AuthenticodeSignature` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2cde0-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="2cde0-189">Verifiera den certifikat utfärdare som har behörighet att signeraren är betrodd.</span><span class="sxs-lookup"><span data-stu-id="2cde0-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="2cde0-190">Hämta modul/resurs beroenden för konfigurationen till en tillfällig plats.</span><span class="sxs-lookup"><span data-stu-id="2cde0-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="2cde0-191">Kontrol lera signaturen för katalogen som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="2cde0-192">Hitta en `<moduleName>.cat` fil och verifiera signaturen med `Get-AuthenticodeSignature`hjälp av.</span><span class="sxs-lookup"><span data-stu-id="2cde0-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="2cde0-193">Verifiera att den certifikat utfärdare som autentiserat signeraren är betrodd.</span><span class="sxs-lookup"><span data-stu-id="2cde0-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="2cde0-194">Kontrol lera att innehållet i modulerna inte har ändrats med den nya cmdleten `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="2cde0-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="2cde0-195">`Install-Module`att`$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="2cde0-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="2cde0-196">Process konfiguration</span><span class="sxs-lookup"><span data-stu-id="2cde0-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="2cde0-197">Verifiering av signaturen för modul-katalog och konfiguration utförs bara när konfigurationen tillämpas på systemet för första gången eller när modulen laddas ned och installeras.</span><span class="sxs-lookup"><span data-stu-id="2cde0-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="2cde0-198">Konsekvens körningar verifierar inte signaturen för current. MOF eller dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="2cde0-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="2cde0-199">Om verifieringen Miss lyckas i något skede, till exempel om konfigurationen som hämtades från hämtnings servern är osignerad, avslutas bearbetningen av konfigurationen med det fel som visas nedan och alla temporära filer tas bort.</span><span class="sxs-lookup"><span data-stu-id="2cde0-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exempel på utdata-konfiguration](media/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="2cde0-201">På samma sätt kan du hämta en modul vars katalog inte är signerade resultat i följande fel:</span><span class="sxs-lookup"><span data-stu-id="2cde0-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Exempel på utdata-modul](media/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="2cde0-203">Push</span><span class="sxs-lookup"><span data-stu-id="2cde0-203">Push</span></span>

<span data-ttu-id="2cde0-204">En konfiguration som levereras med push-teknik kan manipuleras på källan innan den skickas till noden.</span><span class="sxs-lookup"><span data-stu-id="2cde0-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="2cde0-205">Den lokala Configuration Manager utför liknande validerings steg för signaturer för push-eller publicerad konfiguration (er).</span><span class="sxs-lookup"><span data-stu-id="2cde0-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="2cde0-206">Nedan visas ett fullständigt exempel på verifiering av signaturen för push.</span><span class="sxs-lookup"><span data-stu-id="2cde0-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="2cde0-207">Aktivera verifiering av signatur på noden.</span><span class="sxs-lookup"><span data-stu-id="2cde0-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="2cde0-208">Skapa en exempel konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="2cde0-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="2cde0-209">Försök att skicka den osignerade konfigurations filen till noden.</span><span class="sxs-lookup"><span data-stu-id="2cde0-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](media/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="2cde0-211">Signera konfigurations filen med kod signerings certifikat.</span><span class="sxs-lookup"><span data-stu-id="2cde0-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](media/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="2cde0-213">Försök att skicka den signerade MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="2cde0-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](media/DSC-improvements/PushSignedMof.png)
