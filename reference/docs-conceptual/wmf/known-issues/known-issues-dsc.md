---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Desired State Configuration (DSC) Known Issues and Limitations
ms.openlocfilehash: a76c5bb336804c5b384e6b6ba6a705c6049ef7fb
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416603"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="3fecc-103">Desired State Configuration (DSC) Known Issues and Limitations</span><span class="sxs-lookup"><span data-stu-id="3fecc-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="3fecc-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="3fecc-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="3fecc-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span><span class="sxs-lookup"><span data-stu-id="3fecc-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="3fecc-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span><span class="sxs-lookup"><span data-stu-id="3fecc-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="3fecc-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span><span class="sxs-lookup"><span data-stu-id="3fecc-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="3fecc-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="3fecc-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="3fecc-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="3fecc-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="3fecc-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="3fecc-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="3fecc-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span><span class="sxs-lookup"><span data-stu-id="3fecc-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="3fecc-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span><span class="sxs-lookup"><span data-stu-id="3fecc-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="3fecc-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span><span class="sxs-lookup"><span data-stu-id="3fecc-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="3fecc-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span><span class="sxs-lookup"><span data-stu-id="3fecc-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="3fecc-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span><span class="sxs-lookup"><span data-stu-id="3fecc-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="3fecc-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span><span class="sxs-lookup"><span data-stu-id="3fecc-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="3fecc-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fecc-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="3fecc-118">Stop-DscConfiguration may not respond in DebugMode</span><span class="sxs-lookup"><span data-stu-id="3fecc-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="3fecc-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="3fecc-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="3fecc-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="3fecc-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="3fecc-121">No Verbose Error Messages are shown in DebugMode</span><span class="sxs-lookup"><span data-stu-id="3fecc-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="3fecc-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span><span class="sxs-lookup"><span data-stu-id="3fecc-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="3fecc-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span><span class="sxs-lookup"><span data-stu-id="3fecc-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="3fecc-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fecc-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="3fecc-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="3fecc-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="3fecc-126">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="3fecc-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span><span class="sxs-lookup"><span data-stu-id="3fecc-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="3fecc-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span><span class="sxs-lookup"><span data-stu-id="3fecc-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="3fecc-129">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="3fecc-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span><span class="sxs-lookup"><span data-stu-id="3fecc-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="3fecc-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span><span class="sxs-lookup"><span data-stu-id="3fecc-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="3fecc-132">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="3fecc-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="3fecc-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="3fecc-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span><span class="sxs-lookup"><span data-stu-id="3fecc-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="3fecc-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="3fecc-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="3fecc-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span><span class="sxs-lookup"><span data-stu-id="3fecc-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="3fecc-137">Various Partial Configuration documents for same node cannot have identical resource names</span><span class="sxs-lookup"><span data-stu-id="3fecc-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="3fecc-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span><span class="sxs-lookup"><span data-stu-id="3fecc-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="3fecc-139">**Resolution:** Use different names for even same resources in different partial configurations.</span><span class="sxs-lookup"><span data-stu-id="3fecc-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="3fecc-140">Start-DscConfiguration –UseExisting does not work with -Credential</span><span class="sxs-lookup"><span data-stu-id="3fecc-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="3fecc-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span><span class="sxs-lookup"><span data-stu-id="3fecc-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="3fecc-142">DSC uses default process identity to proceed the operation.</span><span class="sxs-lookup"><span data-stu-id="3fecc-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="3fecc-143">This causes error when a different credential is needed to proceed on remote node.</span><span class="sxs-lookup"><span data-stu-id="3fecc-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="3fecc-144">**Resolution:** Use CIM session for remote DSC operations:</span><span class="sxs-lookup"><span data-stu-id="3fecc-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="3fecc-145">IPv6 Addresses as Node Names in DSC configurations</span><span class="sxs-lookup"><span data-stu-id="3fecc-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="3fecc-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span><span class="sxs-lookup"><span data-stu-id="3fecc-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="3fecc-147">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="3fecc-148">Debugging of `Class-Based` DSC Resources</span><span class="sxs-lookup"><span data-stu-id="3fecc-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="3fecc-149">Debugging of class-based DSC Resources is not supported in this release.</span><span class="sxs-lookup"><span data-stu-id="3fecc-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="3fecc-150">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="3fecc-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span><span class="sxs-lookup"><span data-stu-id="3fecc-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="3fecc-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span><span class="sxs-lookup"><span data-stu-id="3fecc-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="3fecc-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span><span class="sxs-lookup"><span data-stu-id="3fecc-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="3fecc-154">No `$script` scope variables/functions.</span><span class="sxs-lookup"><span data-stu-id="3fecc-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="3fecc-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3fecc-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="3fecc-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span><span class="sxs-lookup"><span data-stu-id="3fecc-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="3fecc-157">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="3fecc-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span><span class="sxs-lookup"><span data-stu-id="3fecc-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="3fecc-159">**Resolution:** Use Credential property if available.</span><span class="sxs-lookup"><span data-stu-id="3fecc-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="3fecc-160">Example ServiceSet and WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="3fecc-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="3fecc-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span><span class="sxs-lookup"><span data-stu-id="3fecc-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="3fecc-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span><span class="sxs-lookup"><span data-stu-id="3fecc-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="3fecc-163">**Resolution:** None.</span><span class="sxs-lookup"><span data-stu-id="3fecc-163">**Resolution:** None.</span></span> <span data-ttu-id="3fecc-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3fecc-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="3fecc-165">WindowsOptionalFeature is not available in Windows 7</span><span class="sxs-lookup"><span data-stu-id="3fecc-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="3fecc-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="3fecc-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="3fecc-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span><span class="sxs-lookup"><span data-stu-id="3fecc-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="3fecc-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span><span class="sxs-lookup"><span data-stu-id="3fecc-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="3fecc-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span><span class="sxs-lookup"><span data-stu-id="3fecc-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="3fecc-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span><span class="sxs-lookup"><span data-stu-id="3fecc-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="3fecc-171">Some DSC resources like registry resource may start to take a long time to process the request.</span><span class="sxs-lookup"><span data-stu-id="3fecc-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="3fecc-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span><span class="sxs-lookup"><span data-stu-id="3fecc-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="3fecc-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span><span class="sxs-lookup"><span data-stu-id="3fecc-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
