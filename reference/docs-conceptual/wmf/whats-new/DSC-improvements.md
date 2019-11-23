---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: DSC-förbättringar i WMF 5.1
ms.openlocfilehash: a5efa38ce791a893580316bad7b61a6689153a86
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416669"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="c6aa2-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c6aa2-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="c6aa2-104">DSC class resource improvements</span><span class="sxs-lookup"><span data-stu-id="c6aa2-104">DSC class resource improvements</span></span>

<span data-ttu-id="c6aa2-105">In WMF 5.1, we have fixed the following known issues:</span><span class="sxs-lookup"><span data-stu-id="c6aa2-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="c6aa2-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="c6aa2-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="c6aa2-108">Class-based resource cannot be used in a composite configuration.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="c6aa2-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="c6aa2-110">Class-based resource cannot be used as an exclusive resource.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="c6aa2-111">DSC resource debugging improvements</span><span class="sxs-lookup"><span data-stu-id="c6aa2-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="c6aa2-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="c6aa2-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="c6aa2-114">DSC pull client supports TLS 1.1 and TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="c6aa2-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="c6aa2-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="c6aa2-116">When forced to use more secure protocols, the pull client would stop functioning.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="c6aa2-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="c6aa2-118">Improved pull server registration</span><span class="sxs-lookup"><span data-stu-id="c6aa2-118">Improved pull server registration</span></span>

<span data-ttu-id="c6aa2-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="c6aa2-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span><span class="sxs-lookup"><span data-stu-id="c6aa2-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="c6aa2-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="c6aa2-122">In WMF 5.1, this issue has been fixed.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="c6aa2-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="c6aa2-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="c6aa2-125">Enable Circular log on ESENT database instance</span><span class="sxs-lookup"><span data-stu-id="c6aa2-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="c6aa2-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="c6aa2-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="c6aa2-128">By default CircularLogging is set to TRUE.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="c6aa2-129">WOW64 support for Configuration Keyword</span><span class="sxs-lookup"><span data-stu-id="c6aa2-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="c6aa2-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="c6aa2-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="c6aa2-132">Pull partial configuration naming convention</span><span class="sxs-lookup"><span data-stu-id="c6aa2-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="c6aa2-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="c6aa2-134">See the snapshots below:</span><span class="sxs-lookup"><span data-stu-id="c6aa2-134">See the snapshots below:</span></span>

- <span data-ttu-id="c6aa2-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Sample metaconfiguration](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="c6aa2-137">Sample partial configuration definition</span><span class="sxs-lookup"><span data-stu-id="c6aa2-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="c6aa2-138">'ConfigurationName' embedded in the generated MOF file.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Sample generated mof file](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="c6aa2-140">FileName in the pull configuration repository</span><span class="sxs-lookup"><span data-stu-id="c6aa2-140">FileName in the pull configuration repository</span></span>

  ![FileName in Configuration Repository](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="c6aa2-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="c6aa2-143">So the configuration below compiles to PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="c6aa2-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="c6aa2-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="c6aa2-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="c6aa2-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="c6aa2-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="c6aa2-149">Using PsDscRunAsCredential with DSC composite resources</span><span class="sxs-lookup"><span data-stu-id="c6aa2-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="c6aa2-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="c6aa2-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="c6aa2-152">When specified, all resources run inside a composite resource as a RunAs user.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="c6aa2-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="c6aa2-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="c6aa2-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="c6aa2-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="c6aa2-157">Allowing for Identical Duplicate Resources in a Configuration</span><span class="sxs-lookup"><span data-stu-id="c6aa2-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="c6aa2-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="c6aa2-159">Instead of trying to resolve the conflict, it simply fails.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="c6aa2-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="c6aa2-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="c6aa2-162">With this release, we support having multiple resource instances that have identical definitions:</span><span class="sxs-lookup"><span data-stu-id="c6aa2-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="c6aa2-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="c6aa2-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="c6aa2-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="c6aa2-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="c6aa2-167">DSC module and configuration signing validations</span><span class="sxs-lookup"><span data-stu-id="c6aa2-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="c6aa2-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="c6aa2-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="c6aa2-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="c6aa2-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="c6aa2-172">How to sign configuration and module</span><span class="sxs-lookup"><span data-stu-id="c6aa2-172">How to sign configuration and module</span></span>

- <span data-ttu-id="c6aa2-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="c6aa2-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span><span class="sxs-lookup"><span data-stu-id="c6aa2-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="c6aa2-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="c6aa2-176">Each thumbprint corresponds to a file that is included in the module.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="c6aa2-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="c6aa2-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="c6aa2-179">Place the catalog file inside the module folder.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="c6aa2-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="c6aa2-181">LocalConfigurationManager settings to enable signing validations</span><span class="sxs-lookup"><span data-stu-id="c6aa2-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="c6aa2-182">Pull</span><span class="sxs-lookup"><span data-stu-id="c6aa2-182">Pull</span></span>

<span data-ttu-id="c6aa2-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="c6aa2-184">By default, signature validation is disabled.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="c6aa2-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span><span class="sxs-lookup"><span data-stu-id="c6aa2-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="c6aa2-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="c6aa2-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="c6aa2-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="c6aa2-189">Verify the certificate authority that authorized the signer is trusted.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="c6aa2-190">Download module/resource dependencies of the configuration to a temp location.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="c6aa2-191">Verify the signature of the catalog included inside the module.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="c6aa2-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="c6aa2-193">Verify the certification authority that authenticated the signer is trusted.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="c6aa2-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="c6aa2-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="c6aa2-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="c6aa2-196">Process configuration</span><span class="sxs-lookup"><span data-stu-id="c6aa2-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="c6aa2-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="c6aa2-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="c6aa2-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Sample Error Output Configuration](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="c6aa2-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span><span class="sxs-lookup"><span data-stu-id="c6aa2-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Sample Error Output Module](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="c6aa2-203">Push</span><span class="sxs-lookup"><span data-stu-id="c6aa2-203">Push</span></span>

<span data-ttu-id="c6aa2-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="c6aa2-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span><span class="sxs-lookup"><span data-stu-id="c6aa2-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="c6aa2-206">Below is a complete example of signature validation for push.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="c6aa2-207">Enable signature validation on the node.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="c6aa2-208">Create a sample configuration file.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="c6aa2-209">Try pushing the unsigned configuration file in to the node.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="c6aa2-211">Sign the configuration file using code-signing certificate.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="c6aa2-213">Try pushing the signed MOF file.</span><span class="sxs-lookup"><span data-stu-id="c6aa2-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
