---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell Desired State Configuration partial configurations
ms.openlocfilehash: 379ecf804329f318e9604c1af43a60a0e24551f1
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417737"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="bcaa8-103">PowerShell Desired State Configuration partial configurations</span><span class="sxs-lookup"><span data-stu-id="bcaa8-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="bcaa8-104">_Applies To: Windows PowerShell 5.0 and later._</span><span class="sxs-lookup"><span data-stu-id="bcaa8-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="bcaa8-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="bcaa8-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="bcaa8-107">This capability allows sharing control of configuration between teams or individuals.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="bcaa8-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="bcaa8-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="bcaa8-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="bcaa8-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="bcaa8-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="bcaa8-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="bcaa8-114">Partial configurations in push mode</span><span class="sxs-lookup"><span data-stu-id="bcaa8-114">Partial configurations in push mode</span></span>

<span data-ttu-id="bcaa8-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="bcaa8-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="bcaa8-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="bcaa8-118">Configuring the LCM for push-mode partial configurations</span><span class="sxs-lookup"><span data-stu-id="bcaa8-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="bcaa8-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="bcaa8-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/scripting/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/scripting/dsc/metaConfig).</span></span> <span data-ttu-id="bcaa8-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="bcaa8-122">The **RefreshMode** for each partial configuration is set to "Push".</span><span class="sxs-lookup"><span data-stu-id="bcaa8-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="bcaa8-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="bcaa8-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="bcaa8-125">Publishing and starting push-mode partial configurations</span><span class="sxs-lookup"><span data-stu-id="bcaa8-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="bcaa8-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="bcaa8-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="bcaa8-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="bcaa8-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span><span class="sxs-lookup"><span data-stu-id="bcaa8-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="bcaa8-130">You would publish and run the configurations as follows:</span><span class="sxs-lookup"><span data-stu-id="bcaa8-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="bcaa8-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="bcaa8-132">Partial configurations in pull mode</span><span class="sxs-lookup"><span data-stu-id="bcaa8-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="bcaa8-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="bcaa8-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="bcaa8-135">Configuring the LCM for pull node configurations</span><span class="sxs-lookup"><span data-stu-id="bcaa8-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="bcaa8-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="bcaa8-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="bcaa8-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="bcaa8-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="bcaa8-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="bcaa8-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="bcaa8-142">Configuring the LCM for pull mode configurations using configuration names</span><span class="sxs-lookup"><span data-stu-id="bcaa8-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="bcaa8-143">Configuring the LCM for pull mode configurations using ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="bcaa8-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="bcaa8-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="bcaa8-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="bcaa8-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="bcaa8-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="bcaa8-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="bcaa8-148">Naming configuration documents on the pull server in PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="bcaa8-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="bcaa8-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="bcaa8-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="bcaa8-151">This allows you to pull configurations from Azure Automation DSC pull server.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="bcaa8-152">Naming configuration documents on the pull server in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bcaa8-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="bcaa8-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="bcaa8-154">For our example, the configuration documents should be named as follows:</span><span class="sxs-lookup"><span data-stu-id="bcaa8-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="bcaa8-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="bcaa8-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="bcaa8-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="bcaa8-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="bcaa8-158">For our example, the configuration documents should be named as follows:</span><span class="sxs-lookup"><span data-stu-id="bcaa8-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="bcaa8-159">Running partial configurations from a pull server</span><span class="sxs-lookup"><span data-stu-id="bcaa8-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="bcaa8-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="bcaa8-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="bcaa8-162">Partial configurations in mixed push and pull modes</span><span class="sxs-lookup"><span data-stu-id="bcaa8-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="bcaa8-163">You can also mix push and pull modes for partial configurations.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="bcaa8-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="bcaa8-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="bcaa8-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="bcaa8-167">Mixed push and pull modes using ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="bcaa8-167">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="bcaa8-168">Mixed push and pull modes using ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="bcaa8-168">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="bcaa8-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span><span class="sxs-lookup"><span data-stu-id="bcaa8-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="bcaa8-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span><span class="sxs-lookup"><span data-stu-id="bcaa8-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="bcaa8-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="bcaa8-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="bcaa8-172">Example ServiceAccountConfig Partial Configuration</span><span class="sxs-lookup"><span data-stu-id="bcaa8-172">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="bcaa8-173">Example SharePointConfig Partial Configuration</span><span class="sxs-lookup"><span data-stu-id="bcaa8-173">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="bcaa8-174">Se även</span><span class="sxs-lookup"><span data-stu-id="bcaa8-174">See Also</span></span>

[<span data-ttu-id="bcaa8-175">Windows PowerShell Desired State Configuration Pull Servers</span><span class="sxs-lookup"><span data-stu-id="bcaa8-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="bcaa8-176">Windows Configuring the Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="bcaa8-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
