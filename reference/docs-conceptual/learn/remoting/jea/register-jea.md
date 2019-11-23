---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Registering JEA Configurations
ms.openlocfilehash: dbed5c7dd71f2f7a09d97416be56dff675799548
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417609"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="1131b-103">Registering JEA Configurations</span><span class="sxs-lookup"><span data-stu-id="1131b-103">Registering JEA Configurations</span></span>

<span data-ttu-id="1131b-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="1131b-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span><span class="sxs-lookup"><span data-stu-id="1131b-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="1131b-106">Single machine configuration</span><span class="sxs-lookup"><span data-stu-id="1131b-106">Single machine configuration</span></span>

<span data-ttu-id="1131b-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1131b-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="1131b-108">Before you begin, ensure that the following prerequisites have been met:</span><span class="sxs-lookup"><span data-stu-id="1131b-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="1131b-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span><span class="sxs-lookup"><span data-stu-id="1131b-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="1131b-110">A session configuration file has been created and tested.</span><span class="sxs-lookup"><span data-stu-id="1131b-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="1131b-111">The user registering the JEA configuration has administrator rights on the system.</span><span class="sxs-lookup"><span data-stu-id="1131b-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="1131b-112">You've selected a name for your JEA endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="1131b-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span><span class="sxs-lookup"><span data-stu-id="1131b-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="1131b-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span><span class="sxs-lookup"><span data-stu-id="1131b-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="1131b-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span><span class="sxs-lookup"><span data-stu-id="1131b-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="1131b-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="1131b-117">Run the following command to register the endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1131b-118">The previous command restarts the WinRM service on the system.</span><span class="sxs-lookup"><span data-stu-id="1131b-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="1131b-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span><span class="sxs-lookup"><span data-stu-id="1131b-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="1131b-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span><span class="sxs-lookup"><span data-stu-id="1131b-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="1131b-121">After registration, you're ready to [use JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="1131b-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="1131b-122">You may delete the session configuration file at any time.</span><span class="sxs-lookup"><span data-stu-id="1131b-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="1131b-123">The configuration file isn't used after registration of the endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="1131b-124">Multi-machine configuration with DSC</span><span class="sxs-lookup"><span data-stu-id="1131b-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="1131b-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/scripting/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span><span class="sxs-lookup"><span data-stu-id="1131b-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/scripting/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="1131b-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span><span class="sxs-lookup"><span data-stu-id="1131b-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="1131b-127">One or more role capabilities have been authored and added to a PowerShell module.</span><span class="sxs-lookup"><span data-stu-id="1131b-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="1131b-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span><span class="sxs-lookup"><span data-stu-id="1131b-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="1131b-129">Settings for the session configuration have been determined.</span><span class="sxs-lookup"><span data-stu-id="1131b-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="1131b-130">You don't need to create a session configuration file when using the JEA DSC resource.</span><span class="sxs-lookup"><span data-stu-id="1131b-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="1131b-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span><span class="sxs-lookup"><span data-stu-id="1131b-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="1131b-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="1131b-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="1131b-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span><span class="sxs-lookup"><span data-stu-id="1131b-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="1131b-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span><span class="sxs-lookup"><span data-stu-id="1131b-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="1131b-135">The following properties are configurable using the DSC resource:</span><span class="sxs-lookup"><span data-stu-id="1131b-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="1131b-136">Role Definitions</span><span class="sxs-lookup"><span data-stu-id="1131b-136">Role Definitions</span></span>
- <span data-ttu-id="1131b-137">Virtual account groups</span><span class="sxs-lookup"><span data-stu-id="1131b-137">Virtual account groups</span></span>
- <span data-ttu-id="1131b-138">Group-managed service account name</span><span class="sxs-lookup"><span data-stu-id="1131b-138">Group-managed service account name</span></span>
- <span data-ttu-id="1131b-139">Transcript directory</span><span class="sxs-lookup"><span data-stu-id="1131b-139">Transcript directory</span></span>
- <span data-ttu-id="1131b-140">User drive</span><span class="sxs-lookup"><span data-stu-id="1131b-140">User drive</span></span>
- <span data-ttu-id="1131b-141">Conditional access rules</span><span class="sxs-lookup"><span data-stu-id="1131b-141">Conditional access rules</span></span>
- <span data-ttu-id="1131b-142">Startup scripts for the JEA session</span><span class="sxs-lookup"><span data-stu-id="1131b-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="1131b-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span><span class="sxs-lookup"><span data-stu-id="1131b-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="1131b-144">Below is a sample DSC configuration for a general server maintenance module.</span><span class="sxs-lookup"><span data-stu-id="1131b-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="1131b-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span><span class="sxs-lookup"><span data-stu-id="1131b-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="1131b-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="1131b-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="1131b-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="1131b-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="1131b-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="1131b-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span><span class="sxs-lookup"><span data-stu-id="1131b-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="1131b-150">Unregistering JEA configurations</span><span class="sxs-lookup"><span data-stu-id="1131b-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="1131b-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span><span class="sxs-lookup"><span data-stu-id="1131b-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="1131b-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span><span class="sxs-lookup"><span data-stu-id="1131b-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="1131b-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span><span class="sxs-lookup"><span data-stu-id="1131b-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1131b-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span><span class="sxs-lookup"><span data-stu-id="1131b-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="1131b-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span><span class="sxs-lookup"><span data-stu-id="1131b-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="1131b-156">Only unregister PowerShell endpoints during planned maintenance windows.</span><span class="sxs-lookup"><span data-stu-id="1131b-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1131b-157">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="1131b-157">Next steps</span></span>

[<span data-ttu-id="1131b-158">Test the JEA endpoint</span><span class="sxs-lookup"><span data-stu-id="1131b-158">Test the JEA endpoint</span></span>](using-jea.md)
