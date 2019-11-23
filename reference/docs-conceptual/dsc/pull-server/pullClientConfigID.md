---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417228"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="5fc83-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span><span class="sxs-lookup"><span data-stu-id="5fc83-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="5fc83-104">Applies To: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5fc83-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fc83-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span><span class="sxs-lookup"><span data-stu-id="5fc83-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="5fc83-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="5fc83-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="5fc83-107">Before setting up a pull client, you should set up a pull server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="5fc83-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span><span class="sxs-lookup"><span data-stu-id="5fc83-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="5fc83-109">To set up a pull server, you can use the following guides:</span><span class="sxs-lookup"><span data-stu-id="5fc83-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="5fc83-110">Set up a DSC SMB Pull Server</span><span class="sxs-lookup"><span data-stu-id="5fc83-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="5fc83-111">Set up a DSC HTTP Pull Server</span><span class="sxs-lookup"><span data-stu-id="5fc83-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="5fc83-112">Each target node can be configured to download configurations, resources, and even report its status.</span><span class="sxs-lookup"><span data-stu-id="5fc83-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="5fc83-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="5fc83-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span><span class="sxs-lookup"><span data-stu-id="5fc83-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="5fc83-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span><span class="sxs-lookup"><span data-stu-id="5fc83-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="5fc83-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span><span class="sxs-lookup"><span data-stu-id="5fc83-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="5fc83-117">This topic applies to PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="5fc83-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="5fc83-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="5fc83-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="5fc83-119">Configure the pull client LCM</span><span class="sxs-lookup"><span data-stu-id="5fc83-119">Configure the pull client LCM</span></span>

<span data-ttu-id="5fc83-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span><span class="sxs-lookup"><span data-stu-id="5fc83-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="5fc83-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="5fc83-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="5fc83-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span><span class="sxs-lookup"><span data-stu-id="5fc83-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="5fc83-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="5fc83-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="5fc83-124">Configuration ID</span><span class="sxs-lookup"><span data-stu-id="5fc83-124">Configuration ID</span></span>

<span data-ttu-id="5fc83-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span><span class="sxs-lookup"><span data-stu-id="5fc83-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="5fc83-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="5fc83-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span><span class="sxs-lookup"><span data-stu-id="5fc83-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="5fc83-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="5fc83-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="5fc83-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fc83-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="5fc83-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="5fc83-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="5fc83-131">Set up a Pull Client to download Configurations</span><span class="sxs-lookup"><span data-stu-id="5fc83-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="5fc83-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span><span class="sxs-lookup"><span data-stu-id="5fc83-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="5fc83-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span><span class="sxs-lookup"><span data-stu-id="5fc83-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="5fc83-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span><span class="sxs-lookup"><span data-stu-id="5fc83-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="5fc83-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="5fc83-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="5fc83-136">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="5fc83-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="5fc83-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="5fc83-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="5fc83-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="5fc83-139">The **ServerUrl** specifies the url of the DSC Pull</span><span class="sxs-lookup"><span data-stu-id="5fc83-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="5fc83-140">SMB Share</span><span class="sxs-lookup"><span data-stu-id="5fc83-140">SMB Share</span></span>

<span data-ttu-id="5fc83-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="5fc83-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="5fc83-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span><span class="sxs-lookup"><span data-stu-id="5fc83-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="5fc83-143">Set up a Pull Client to download Resources</span><span class="sxs-lookup"><span data-stu-id="5fc83-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="5fc83-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span><span class="sxs-lookup"><span data-stu-id="5fc83-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="5fc83-145">You can also specify separate locations for resources.</span><span class="sxs-lookup"><span data-stu-id="5fc83-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="5fc83-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="5fc83-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="5fc83-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="5fc83-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="5fc83-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="5fc83-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="5fc83-149">Examples of this are not shown below.</span><span class="sxs-lookup"><span data-stu-id="5fc83-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="5fc83-150">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="5fc83-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="5fc83-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="5fc83-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="5fc83-152">SMB Share</span><span class="sxs-lookup"><span data-stu-id="5fc83-152">SMB Share</span></span>

<span data-ttu-id="5fc83-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="5fc83-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="5fc83-154">Automatically download Resources in Push Mode</span><span class="sxs-lookup"><span data-stu-id="5fc83-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="5fc83-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span><span class="sxs-lookup"><span data-stu-id="5fc83-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="5fc83-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="5fc83-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="5fc83-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="5fc83-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="5fc83-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="5fc83-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span><span class="sxs-lookup"><span data-stu-id="5fc83-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="5fc83-160">Set up a Pull Client to report status</span><span class="sxs-lookup"><span data-stu-id="5fc83-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="5fc83-161">By default, Nodes will not send reports to a configured Pull Server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="5fc83-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span><span class="sxs-lookup"><span data-stu-id="5fc83-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="5fc83-163">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="5fc83-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="5fc83-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="5fc83-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="5fc83-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="5fc83-166">A report server cannot be an SMB server.</span><span class="sxs-lookup"><span data-stu-id="5fc83-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="5fc83-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="5fc83-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="5fc83-168">SMB Share</span><span class="sxs-lookup"><span data-stu-id="5fc83-168">SMB Share</span></span>

<span data-ttu-id="5fc83-169">A report server cannot be an SMB share.</span><span class="sxs-lookup"><span data-stu-id="5fc83-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5fc83-170">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="5fc83-170">Next Steps</span></span>

<span data-ttu-id="5fc83-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span><span class="sxs-lookup"><span data-stu-id="5fc83-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="5fc83-172">Publish Configurations to a Pull Server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="5fc83-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="5fc83-173">Package and Upload Resources to a Pull Server (v4)</span><span class="sxs-lookup"><span data-stu-id="5fc83-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="5fc83-174">Se även</span><span class="sxs-lookup"><span data-stu-id="5fc83-174">See Also</span></span>

* [<span data-ttu-id="5fc83-175">Setting up a pull client with configuration names</span><span class="sxs-lookup"><span data-stu-id="5fc83-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
