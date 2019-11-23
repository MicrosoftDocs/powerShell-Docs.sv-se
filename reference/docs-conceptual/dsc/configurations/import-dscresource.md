---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Använda Import-DSCResource
ms.openlocfilehash: 4bc269ab1dd4696298b4f33f7661473aae869eba
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417419"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="fae4d-103">Använda Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="fae4d-103">Using Import-DSCResource</span></span>

<span data-ttu-id="fae4d-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span><span class="sxs-lookup"><span data-stu-id="fae4d-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="fae4d-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span><span class="sxs-lookup"><span data-stu-id="fae4d-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="fae4d-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="fae4d-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="fae4d-107">The syntax for `Import-DSCResource` is shown below.</span><span class="sxs-lookup"><span data-stu-id="fae4d-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="fae4d-108">When specifying modules by name, it is a requirement to list each on a new line.</span><span class="sxs-lookup"><span data-stu-id="fae4d-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="fae4d-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="fae4d-109">Parameter</span></span>  |<span data-ttu-id="fae4d-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fae4d-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="fae4d-111">The DSC resource name(s) that you must import.</span><span class="sxs-lookup"><span data-stu-id="fae4d-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="fae4d-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span><span class="sxs-lookup"><span data-stu-id="fae4d-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="fae4d-113">Wildcards are supported.</span><span class="sxs-lookup"><span data-stu-id="fae4d-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="fae4d-114">The module name, or module specification.</span><span class="sxs-lookup"><span data-stu-id="fae4d-114">The module name, or module specification.</span></span>  <span data-ttu-id="fae4d-115">If you specify resources to import from a module, the command will try to import only those resources.</span><span class="sxs-lookup"><span data-stu-id="fae4d-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="fae4d-116">If you specify the module only, the command imports all the DSC resources in the module.</span><span class="sxs-lookup"><span data-stu-id="fae4d-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="fae4d-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span><span class="sxs-lookup"><span data-stu-id="fae4d-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="fae4d-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="fae4d-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="fae4d-119">Example: Use Import-DSCResource within a configuration</span><span class="sxs-lookup"><span data-stu-id="fae4d-119">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="fae4d-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span><span class="sxs-lookup"><span data-stu-id="fae4d-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="fae4d-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span><span class="sxs-lookup"><span data-stu-id="fae4d-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="fae4d-122">Below command will result in error during compilation.</span><span class="sxs-lookup"><span data-stu-id="fae4d-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="fae4d-123">Things to consider when using only the Name parameter:</span><span class="sxs-lookup"><span data-stu-id="fae4d-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="fae4d-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span><span class="sxs-lookup"><span data-stu-id="fae4d-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="fae4d-125">It will load the first resource found with the given name.</span><span class="sxs-lookup"><span data-stu-id="fae4d-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="fae4d-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span><span class="sxs-lookup"><span data-stu-id="fae4d-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="fae4d-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span><span class="sxs-lookup"><span data-stu-id="fae4d-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="fae4d-128">This usage has the following benefits:</span><span class="sxs-lookup"><span data-stu-id="fae4d-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="fae4d-129">It reduces the performance impact by limiting the search scope for the specified resource.</span><span class="sxs-lookup"><span data-stu-id="fae4d-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="fae4d-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span><span class="sxs-lookup"><span data-stu-id="fae4d-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="fae4d-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span><span class="sxs-lookup"><span data-stu-id="fae4d-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="fae4d-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span><span class="sxs-lookup"><span data-stu-id="fae4d-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="fae4d-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="fae4d-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="fae4d-134">Intellisense with Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="fae4d-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="fae4d-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span><span class="sxs-lookup"><span data-stu-id="fae4d-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="fae4d-136">Resource definitions under the `$pshome` module path are loaded automatically.</span><span class="sxs-lookup"><span data-stu-id="fae4d-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="fae4d-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span><span class="sxs-lookup"><span data-stu-id="fae4d-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Resource Intellisense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="fae4d-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span><span class="sxs-lookup"><span data-stu-id="fae4d-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="fae4d-140">For more information, see [Resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="fae4d-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="fae4d-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span><span class="sxs-lookup"><span data-stu-id="fae4d-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="fae4d-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span><span class="sxs-lookup"><span data-stu-id="fae4d-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="fae4d-143">Only properties defined in schema are used.</span><span class="sxs-lookup"><span data-stu-id="fae4d-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="fae4d-144">The data types for each property are correct.</span><span class="sxs-lookup"><span data-stu-id="fae4d-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="fae4d-145">Keys properties are specified.</span><span class="sxs-lookup"><span data-stu-id="fae4d-145">Keys properties are specified.</span></span>
- <span data-ttu-id="fae4d-146">No read-only property is used.</span><span class="sxs-lookup"><span data-stu-id="fae4d-146">No read-only property is used.</span></span>
- <span data-ttu-id="fae4d-147">Validation on value maps types.</span><span class="sxs-lookup"><span data-stu-id="fae4d-147">Validation on value maps types.</span></span>

<span data-ttu-id="fae4d-148">Consider the following configuration:</span><span class="sxs-lookup"><span data-stu-id="fae4d-148">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="fae4d-149">Compiling this Configuration results in an error.</span><span class="sxs-lookup"><span data-stu-id="fae4d-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="fae4d-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span><span class="sxs-lookup"><span data-stu-id="fae4d-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="fae4d-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span><span class="sxs-lookup"><span data-stu-id="fae4d-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="fae4d-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="fae4d-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="fae4d-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span><span class="sxs-lookup"><span data-stu-id="fae4d-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="fae4d-154">PowerShell v4 and v5 differences</span><span class="sxs-lookup"><span data-stu-id="fae4d-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="fae4d-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span><span class="sxs-lookup"><span data-stu-id="fae4d-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="fae4d-156">This section will highlight the differences that you see relevant to this article.</span><span class="sxs-lookup"><span data-stu-id="fae4d-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="fae4d-157">Multiple Resource Versions</span><span class="sxs-lookup"><span data-stu-id="fae4d-157">Multiple Resource Versions</span></span>

<span data-ttu-id="fae4d-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="fae4d-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="fae4d-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span><span class="sxs-lookup"><span data-stu-id="fae4d-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="fae4d-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span><span class="sxs-lookup"><span data-stu-id="fae4d-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Multiple Resource Versions Fixed](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="fae4d-162">Copy the contents of your desired module version to the top level of the module directory.</span><span class="sxs-lookup"><span data-stu-id="fae4d-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Multiple Resource Versions Fixed](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="fae4d-164">Resource location</span><span class="sxs-lookup"><span data-stu-id="fae4d-164">Resource location</span></span>

<span data-ttu-id="fae4d-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="fae4d-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="fae4d-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="fae4d-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="fae4d-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="fae4d-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="fae4d-168">ModuleVersion added</span><span class="sxs-lookup"><span data-stu-id="fae4d-168">ModuleVersion added</span></span>

<span data-ttu-id="fae4d-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span><span class="sxs-lookup"><span data-stu-id="fae4d-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="fae4d-170">Se även</span><span class="sxs-lookup"><span data-stu-id="fae4d-170">See also</span></span>

- [<span data-ttu-id="fae4d-171">Resurser</span><span class="sxs-lookup"><span data-stu-id="fae4d-171">Resources</span></span>](../resources/resources.md)
