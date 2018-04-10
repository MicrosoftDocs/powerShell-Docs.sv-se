---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: DSC-förbättringar i WMF 5.1
ms.openlocfilehash: 04bf8ed820d24f1062e05d19c8f3b0c041298979
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="c31e4-103">Förbättringar i Desired State Configuration (DSC) i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c31e4-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="c31e4-104">Förbättringar av DSC-klassen resurs</span><span class="sxs-lookup"><span data-stu-id="c31e4-104">DSC class resource improvements</span></span>

<span data-ttu-id="c31e4-105">Vi har löst följande kända problem i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="c31e4-105">In WMF 5.1, we have fixed the following known issues:</span></span>
* <span data-ttu-id="c31e4-106">Get-DscConfiguration kan returnera tomma värden (null) eller fel om en komplex/hash-tabelltyp returneras av Get()-funktionen för en klass-baserade DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="c31e4-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
* <span data-ttu-id="c31e4-107">Get-DscConfiguration returnerar fel om RunAs-autentiseringsuppgift används i DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
* <span data-ttu-id="c31e4-108">Klass-baserade resursen kan inte användas i en sammansatt konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c31e4-108">Class-based resource cannot be used in a composite configuration.</span></span>
* <span data-ttu-id="c31e4-109">Start-DscConfiguration låser sig om klass-baserade resursen har en egenskap för sin egen typ.</span><span class="sxs-lookup"><span data-stu-id="c31e4-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
* <span data-ttu-id="c31e4-110">Klass-baserade resursen kan inte användas som en exklusiv resurs.</span><span class="sxs-lookup"><span data-stu-id="c31e4-110">Class-based resource cannot be used as an exclusive resource.</span></span>


## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="c31e4-111">DSC-resurs felsökning förbättringar</span><span class="sxs-lookup"><span data-stu-id="c31e4-111">DSC resource debugging improvements</span></span>
<span data-ttu-id="c31e4-112">I WMF 5.0 stoppades PowerShell felsökningsprogrammet inte på klass-baserade resurs-metoden (Get och Set/testning) direkt.</span><span class="sxs-lookup"><span data-stu-id="c31e4-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="c31e4-113">WMF 5.1 slutar felsökningsprogrammet vid klass-baserade resurs-metod på samma sätt som för MOF-baserade resurser metoder.</span><span class="sxs-lookup"><span data-stu-id="c31e4-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="c31e4-114">DSC pull-klienten har stöd för TLS 1.1 och TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="c31e4-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>
<span data-ttu-id="c31e4-115">Tidigare stöds DSC pull-klienten endast SSL3.0 och TLS1.0 över HTTPS-anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c31e4-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="c31e4-116">När tvungen att använda säkrare protokoll, skulle pull-klienten sluta fungera.</span><span class="sxs-lookup"><span data-stu-id="c31e4-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="c31e4-117">I WMF 5.1 DSC pull klienten inte längre har stöd för SSL 3.0 och lägger till stöd för protokollen säkrare TLS 1.1 och TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="c31e4-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="c31e4-118">Registrera för förbättrad pull-servern</span><span class="sxs-lookup"><span data-stu-id="c31e4-118">Improved pull server registration</span></span> ##

<span data-ttu-id="c31e4-119">I tidigare versioner av WMF skulle samtidiga registreringar/rapportering begäranden till DSC pull-servern när du använder ESENT-databasen leda till MGM om du inte kan registrera och/eller rapportera.</span><span class="sxs-lookup"><span data-stu-id="c31e4-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="c31e4-120">I sådana fall händelseloggarna på hämtningsservern har felet ”instansnamnet används redan”.</span><span class="sxs-lookup"><span data-stu-id="c31e4-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="c31e4-121">Detta beror på ett felaktigt mönster som används för att få åtkomst till ESENT-databasen i ett flertrådat scenario.</span><span class="sxs-lookup"><span data-stu-id="c31e4-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="c31e4-122">Det här problemet har åtgärdats i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="c31e4-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="c31e4-123">Samtidiga registreringar eller rapportering (som involverar ESENT databasen) fungerar bra i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="c31e4-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="c31e4-124">Det här problemet gäller endast för ESENT-databasen och gäller inte för OLEDB-databasen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="c31e4-125">Aktivera cirkulär inloggning ESENT-databasinstans</span><span class="sxs-lookup"><span data-stu-id="c31e4-125">Enable Circular log on ESENT database instance</span></span>
<span data-ttu-id="c31e4-126">I eariler versionen av DSC-PullServer, ESENT loggfiler fyller upp diskutrymme på den pullserver becouse databasinstansen skapades utan cirkulär loggning.</span><span class="sxs-lookup"><span data-stu-id="c31e4-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="c31e4-127">I den här versionen har du möjlighet att styra instansen med hjälp av web.config i pullserver cirkulär loggning.</span><span class="sxs-lookup"><span data-stu-id="c31e4-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="c31e4-128">Som standard anges CircularLogging till SANT.</span><span class="sxs-lookup"><span data-stu-id="c31e4-128">By default CircularLogging is set to TRUE.</span></span>
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="c31e4-129">Hämta partiella configuration namngivningskonvention</span><span class="sxs-lookup"><span data-stu-id="c31e4-129">Pull partial configuration naming convention</span></span>
<span data-ttu-id="c31e4-130">I den tidigare versionen har en partiell konfiguration namngivningskonvention att MOF-filens namn i pull/tjänsten server ska matcha partiella Konfigurationsnamnet anges i inställningarna för lokala configuration manager som i sin tur måste matcha den Konfigurationsnamnet inbäddade i MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="c31e4-131">Se ögonblicksbilder nedan:</span><span class="sxs-lookup"><span data-stu-id="c31e4-131">See the snapshots below:</span></span>

<span data-ttu-id="c31e4-132">• Lokala konfigurationsinställningar som definierar en partiell konfiguration som en nod kan ta emot.</span><span class="sxs-lookup"><span data-stu-id="c31e4-132">•   Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Exempel metakonfigurationen](../images/MetaConfigPartialOne.png)

<span data-ttu-id="c31e4-134">• Exempel partiella konfigurationsdefinition</span><span class="sxs-lookup"><span data-stu-id="c31e4-134">•   Sample partial configuration definition</span></span>

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

<span data-ttu-id="c31e4-135">• 'ConfigurationName' inbäddade i genererade MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-135">•   'ConfigurationName' embedded in the generated MOF file.</span></span>

![Exempel genererade mof-filen](../images/PartialGeneratedMof.png)

<span data-ttu-id="c31e4-137">• Filnamn i databasen för pull-konfiguration</span><span class="sxs-lookup"><span data-stu-id="c31e4-137">•   FileName in the pull configuration repository</span></span>

![Filnamn i konfiguration av databas](../images/PartialInConfigRepository.png)

<span data-ttu-id="c31e4-139">Azure Automation-tjänstnamnet genereras MOF-filer som `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="c31e4-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="c31e4-140">Konfigurationen nedan sammanfattar så att PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="c31e4-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="c31e4-141">Detta har gjort det omöjligt att dra en partiell konfigurationen från Azure Automation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c31e4-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="c31e4-142">I WMF 5.1 en partiell konfiguration i pull/tjänsten server kan namnges som `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="c31e4-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="c31e4-143">Om en dator är att använda en enda konfigurationen från en pull kan dessutom/servertjänsten sedan konfigurationsfilen på pull server configuration databasen ha ett filnamn.</span><span class="sxs-lookup"><span data-stu-id="c31e4-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="c31e4-144">Namngivning flexibilitet kan du hantera noderna delvis av Azure Automation-tjänsten, där vissa konfigurationsinställningar för noden kommer från Azure Automation DSC och med en partiell konfiguration som du hanterar lokalt.</span><span class="sxs-lookup"><span data-stu-id="c31e4-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="c31e4-145">Metakonfigurationen nedan ställer in en nod ska hanteras både lokalt som med Azure Automation-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c31e4-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="c31e4-146">Med hjälp av PsDscRunAsCredential med sammansatta DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="c31e4-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="c31e4-147">Vi har lagt till stöd för användning av [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) med DSC [sammansatta](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resurser.</span><span class="sxs-lookup"><span data-stu-id="c31e4-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="c31e4-148">Du kan ange ett värde för PsDscRunAsCredential när du använder sammansatta resurser inuti konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="c31e4-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="c31e4-149">När anges körs alla resurser i en sammansatt resurs som en RunAs-användare.</span><span class="sxs-lookup"><span data-stu-id="c31e4-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="c31e4-150">Om en sammansatt resurs anrop till en annan sammansatta resurs kan köra alla dess resurser även som RunAs-användare.</span><span class="sxs-lookup"><span data-stu-id="c31e4-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="c31e4-151">RunAs-autentiseringsuppgifterna sprids till valfri nivå i hierarkin sammansatta resurs.</span><span class="sxs-lookup"><span data-stu-id="c31e4-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="c31e4-152">Om en resurs i en sammansatt resurs anger sitt eget värde för PsDscRunAsCredential, resulterar en merge-fel under kompilering av konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c31e4-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="c31e4-153">Det här exemplet visar användningen med [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) sammansatta resurs som ingår i PSDesiredStateConfiguration modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>



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

##<a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="c31e4-154">DSC-modulen och signering verifieringar-konfiguration</span><span class="sxs-lookup"><span data-stu-id="c31e4-154">DSC module and configuration signing validations</span></span>
<span data-ttu-id="c31e4-155">I DSC distribueras konfigurationer och moduler till hanterade datorer från hämtningsservern i.</span><span class="sxs-lookup"><span data-stu-id="c31e4-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="c31e4-156">Om pull-servern har komprometterats bör en angripare ändra konfigurationer och moduler på hämtningsservern potentiellt och har distribuerats till alla hanterade noder, kompromettera alla.</span><span class="sxs-lookup"><span data-stu-id="c31e4-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

 <span data-ttu-id="c31e4-157">I WMF 5.1 DSC stöder verifierar digitala signaturer i katalogen och konfiguration (. MOF)-filer.</span><span class="sxs-lookup"><span data-stu-id="c31e4-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="c31e4-158">Den här funktionen förhindrar att noder körning konfigurationer eller modulen filer som inte har signerats av en betrodd undertecknare eller som har ändrats efter att de har signerats av betrodda undertecknare.</span><span class="sxs-lookup"><span data-stu-id="c31e4-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>



###<a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="c31e4-159">Hur du registrerar konfiguration och modulen</span><span class="sxs-lookup"><span data-stu-id="c31e4-159">How to sign configuration and module</span></span>
***
* <span data-ttu-id="c31e4-160">Konfigurationsfiler (. MOF-filer): befintliga PowerShell-cmdleten [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) är utökat stöd för signering av MOF-filer.</span><span class="sxs-lookup"><span data-stu-id="c31e4-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="c31e4-161">Moduler: Signering av moduler görs genom att registrera den motsvarande modul-katalog med följande steg:</span><span class="sxs-lookup"><span data-stu-id="c31e4-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="c31e4-162">Skapa en katalogfil: en katalogfil innehåller en uppsättning kryptografiska hash-värden eller tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="c31e4-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="c31e4-163">Varje tumavtrycket motsvarar en fil som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="c31e4-164">Följande nya cmdlet [ny FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), har lagts till kan du skapa en katalogfil för sina modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="c31e4-165">Signera katalogfilen: Använd [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) att signera katalogfilen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="c31e4-166">Placera katalogfilen i mappen som modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="c31e4-167">Enligt konventionen är placeras modulen katalogfil under mappen modulen med samma namn som modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="c31e4-168">LocalConfigurationManager inställningar för att aktivera signering verifieringar</span><span class="sxs-lookup"><span data-stu-id="c31e4-168">LocalConfigurationManager settings to enable signing validations</span></span>

####<a name="pull"></a><span data-ttu-id="c31e4-169">Hämtar</span><span class="sxs-lookup"><span data-stu-id="c31e4-169">Pull</span></span>
<span data-ttu-id="c31e4-170">LocalConfigurationManager för en nod utför signering validering av moduler och konfigurationer baserat på de aktuella inställningarna.</span><span class="sxs-lookup"><span data-stu-id="c31e4-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="c31e4-171">Signaturverifiering är inaktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="c31e4-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="c31e4-172">Signaturverifiering kan aktiveras genom att lägga till blockeringen 'SignatureValidation' meta-konfigurationsdefinition för noden som visas nedan:</span><span class="sxs-lookup"><span data-stu-id="c31e4-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
 ```

<span data-ttu-id="c31e4-173">Anger ovan metakonfigurationen på en nod kan verifiera signaturen på hämtade konfigurationer och moduler.</span><span class="sxs-lookup"><span data-stu-id="c31e4-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="c31e4-174">Local Configuration Manager utför följande steg för att verifiera de digitala signaturerna.</span><span class="sxs-lookup"><span data-stu-id="c31e4-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="c31e4-175">Verifiera signaturen på en konfigurationsfil (. MOF) är giltig.</span><span class="sxs-lookup"><span data-stu-id="c31e4-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="c31e4-176">Den använder du PowerShell-cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), som utökas i 5.1 att stödja MOF signaturverifiering.</span><span class="sxs-lookup"><span data-stu-id="c31e4-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="c31e4-177">Kontrollera som auktoriserad undertecknarens certifikatutfärdaren är betrodd.</span><span class="sxs-lookup"><span data-stu-id="c31e4-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="c31e4-178">Hämta modul/resursberoenden av konfigurationen till en tillfällig plats.</span><span class="sxs-lookup"><span data-stu-id="c31e4-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="c31e4-179">Verifiera signaturen på den katalog som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="c31e4-180">Hitta en `<moduleName>.cat` och kontrollera att signaturen med hjälp av cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="c31e4-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="c31e4-181">Kontrollera den certifikatutfärdare som autentiseras undertecknarens är betrodd.</span><span class="sxs-lookup"><span data-stu-id="c31e4-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="c31e4-182">Kontrollera innehållet i modulerna som inte har ändrats med nya cmdlet [Test FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="c31e4-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="c31e4-183">Installera modulen till $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="c31e4-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="c31e4-184">Processkonfiguration</span><span class="sxs-lookup"><span data-stu-id="c31e4-184">Process configuration</span></span>

> <span data-ttu-id="c31e4-185">Obs: Signaturverifiering på modul-katalog och konfiguration utförs endast när konfigurationen tillämpas i systemet för första gången eller när modulen hämtas och installeras.</span><span class="sxs-lookup"><span data-stu-id="c31e4-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="c31e4-186">Konsekvenskontroll körs validerar inte signaturen för Current.mof eller dess beroenden i modulen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="c31e4-187">Om det gick inte att verifiera när som helst, till exempel om konfigurationen hämtas från pull-servern är osignerat, sedan bearbetning av konfigurationen avslutas med felet visas nedan och alla temporära filer tas bort.</span><span class="sxs-lookup"><span data-stu-id="c31e4-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exempelkonfiguration fel utdata](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="c31e4-189">På liknande sätt kan signerat dra en modul vars katalogen inte är resulterar i följande fel:</span><span class="sxs-lookup"><span data-stu-id="c31e4-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Exempel Felmodulen för utdata](../images/PullUnisgnedCatalog.png)

####<a name="push"></a><span data-ttu-id="c31e4-191">Push</span><span class="sxs-lookup"><span data-stu-id="c31e4-191">Push</span></span>
<span data-ttu-id="c31e4-192">En konfiguration som levereras med hjälp av push kan vara har manipulerats på källan innan det levereras till noden.</span><span class="sxs-lookup"><span data-stu-id="c31e4-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="c31e4-193">Local Configuration Manager utför liknande steg för verifiering av signatur för intryckt eller publicerade konfiguration(er).</span><span class="sxs-lookup"><span data-stu-id="c31e4-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="c31e4-194">Nedan visas en komplett exempel på signaturvalidering för distribution.</span><span class="sxs-lookup"><span data-stu-id="c31e4-194">Below is a complete example of signature validation for push.</span></span>

* <span data-ttu-id="c31e4-195">Aktivera signaturverifiering på noden.</span><span class="sxs-lookup"><span data-stu-id="c31e4-195">Enable signature validation on the node.</span></span>

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
* <span data-ttu-id="c31e4-196">Skapa en exempelfil i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-196">Create a sample configuration file.</span></span>

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

* <span data-ttu-id="c31e4-197">Försök att överföra osignerade konfigurationsfilen till noden.</span><span class="sxs-lookup"><span data-stu-id="c31e4-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* <span data-ttu-id="c31e4-199">Logga konfigurationsfilen med kodsigneringscertifikat.</span><span class="sxs-lookup"><span data-stu-id="c31e4-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

* <span data-ttu-id="c31e4-201">Försök att överföra den signerade MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="c31e4-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)