---
ms.date: 07/23/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-resurser
description: DSC-resurser tillhandahåller Bygg stenar för en DSC-konfiguration. En resurs exponerar egenskaper som kan konfigureras (schema) och innehåller de PowerShell-skript funktioner som används av LCM för att tillämpa konfigurationen.
ms.openlocfilehash: 1634db84deff8de3b33c941ad738dc21cf3017ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658445"
---
# <a name="dsc-resources"></a><span data-ttu-id="91b02-105">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="91b02-105">DSC Resources</span></span>

> <span data-ttu-id="91b02-106">Gäller för Windows PowerShell 4,0 och uppåt.</span><span class="sxs-lookup"><span data-stu-id="91b02-106">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="91b02-107">Översikt</span><span class="sxs-lookup"><span data-stu-id="91b02-107">Overview</span></span>

<span data-ttu-id="91b02-108">DSC-resurser (Desired State Configuration) tillhandahåller Bygg stenar för en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="91b02-108">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="91b02-109">En resurs exponerar egenskaper som kan konfigureras (schema) och innehåller PowerShell-skript som de lokala Configuration Manager (LCM) anropar för att göra det.</span><span class="sxs-lookup"><span data-stu-id="91b02-109">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="91b02-110">En resurs kan modellera något som generiskt som en fil eller som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="91b02-110">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="91b02-111">Grupper av resurser som är kombinerade i till en DSC-modul som organiserar alla nödvändiga filer i en struktur som är portabel och innehåller metadata för att identifiera hur resurserna är avsedda att användas.</span><span class="sxs-lookup"><span data-stu-id="91b02-111">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="91b02-112">Varje resurs har ett \*-schema som avgör den syntax som behövs för att använda resursen i en [konfiguration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="91b02-112">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="91b02-113">En resurs schema kan definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="91b02-113">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="91b02-114">`Schema.Mof` fil: de flesta resurser definierar _schemat_ i en `schema.mof` fil med hjälp av [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="91b02-114">`Schema.Mof` file: Most resources define their _schema_ in a `schema.mof` file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="91b02-115">`<Resource Name>.schema.psm1` fil: [sammansatta resurser](../configurations/compositeConfigs.md) definierar deras _schema_ i en `<ResourceName>.schema.psm1` fil med hjälp av ett [parameter block](/powershell/module/microsoft.powershell.core/about/about_functions#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="91b02-115">`<Resource Name>.schema.psm1` file: [Composite Resources](../configurations/compositeConfigs.md) define their _schema_ in a `<ResourceName>.schema.psm1` file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions#functions-with-parameters).</span></span>
- <span data-ttu-id="91b02-116">`<Resource Name>.psm1` fil: klassbaserade DSC-resurser definierar deras _schema_ i klass definitionen.</span><span class="sxs-lookup"><span data-stu-id="91b02-116">`<Resource Name>.psm1` file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="91b02-117">Objekt betecknas som klass egenskaper.</span><span class="sxs-lookup"><span data-stu-id="91b02-117">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="91b02-118">Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="91b02-118">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="91b02-119">Om du vill hämta syntaxen för en DSC-resurs använder du cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) med parametern **syntax** .</span><span class="sxs-lookup"><span data-stu-id="91b02-119">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the **Syntax** parameter.</span></span> <span data-ttu-id="91b02-120">Den här användningen liknar att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med parametern **syntax** för att hämta cmdlet-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="91b02-120">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the **Syntax** parameter to get cmdlet syntax.</span></span> <span data-ttu-id="91b02-121">De utdata som visas visar den mall som används för ett resurs block för den resurs som du anger.</span><span class="sxs-lookup"><span data-stu-id="91b02-121">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="91b02-122">De utdata du ser liknar utdata nedan, men den här resursens syntax kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="91b02-122">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="91b02-123">Precis som cmdlet-syntaxen är de _nycklar_ som visas i hakparenteser valfria.</span><span class="sxs-lookup"><span data-stu-id="91b02-123">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="91b02-124">Typerna anger vilken typ av data varje nyckel förväntar sig.</span><span class="sxs-lookup"><span data-stu-id="91b02-124">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="91b02-125">Nyckeln **säkerställer att** nyckeln är valfri eftersom den används som standard.</span><span class="sxs-lookup"><span data-stu-id="91b02-125">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

> [!NOTE]
> <span data-ttu-id="91b02-126">I PowerShell-versioner under 7,0 `Get-DscResource` hittar du inte klassbaserade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="91b02-126">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="91b02-127">I en konfiguration kan ett **tjänst** resurs block se ut så här för att **säkerställa** att Spooler-tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="91b02-127">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="91b02-128">Innan du använder en resurs i en konfiguration måste du importera den med hjälp av [import-dscresource Keyword Supports](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="91b02-128">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the
    # resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as l
        # ong as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="91b02-129">Konfigurationer kan innehålla flera instanser av samma resurs typ.</span><span class="sxs-lookup"><span data-stu-id="91b02-129">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="91b02-130">Varje instans måste ha ett unikt namn.</span><span class="sxs-lookup"><span data-stu-id="91b02-130">Each instance must be uniquely named.</span></span> <span data-ttu-id="91b02-131">I följande exempel läggs ett andra **tjänst** resurs block till för att konfigurera tjänsten "DHCP".</span><span class="sxs-lookup"><span data-stu-id="91b02-131">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the
    # resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as
        # long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service
        # resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="91b02-132">Från och med PowerShell 5,0 lades IntelliSense till för DSC.</span><span class="sxs-lookup"><span data-stu-id="91b02-132">Beginning in PowerShell 5.0, IntelliSense was added for DSC.</span></span> <span data-ttu-id="91b02-133">Med den här nya funktionen kan du <kbd>TAB</kbd> använda TABB <kbd>-och</kbd> + <kbd>rymd utrymme</kbd> för att komplettera nyckel namn automatiskt.</span><span class="sxs-lookup"><span data-stu-id="91b02-133">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![Resurs-IntelliSense med tabb-slutförande](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="91b02-135">Typer av resurser</span><span class="sxs-lookup"><span data-stu-id="91b02-135">Types of resources</span></span>

<span data-ttu-id="91b02-136">Windows levereras med inbyggda resurser och Linux har leverantörsspecifika resurser.</span><span class="sxs-lookup"><span data-stu-id="91b02-136">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="91b02-137">Det finns resurser för [över-nod-beroenden](../configurations/crossNodeDependencies.md), paket hanterings resurser samt[ägda och bevarade resurser](https://github.com/dsccommunity).</span><span class="sxs-lookup"><span data-stu-id="91b02-137">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="91b02-138">Du kan använda ovanstående steg för att fastställa syntaxen för dessa resurser och hur du använder dem.</span><span class="sxs-lookup"><span data-stu-id="91b02-138">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="91b02-139">De sidor som hanterar dessa resurser har arkiverats under **referens** .</span><span class="sxs-lookup"><span data-stu-id="91b02-139">The pages that serve these resources have been archived under **Reference** .</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="91b02-140">Inbyggda resurser i Windows</span><span class="sxs-lookup"><span data-stu-id="91b02-140">Windows built-in resources</span></span>

- [<span data-ttu-id="91b02-141">Arkivera resursen</span><span class="sxs-lookup"><span data-stu-id="91b02-141">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="91b02-142">Miljöresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-142">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="91b02-143">Filresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-143">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="91b02-144">Gruppresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-144">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="91b02-145">GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-145">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="91b02-146">Loggresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-146">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="91b02-147">Paketresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-147">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="91b02-148">ProcessSet-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-148">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="91b02-149">Registerresurser</span><span class="sxs-lookup"><span data-stu-id="91b02-149">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="91b02-150">Skriptresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-150">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="91b02-151">Tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-151">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="91b02-152">ServiceSet-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-152">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="91b02-153">Användarresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-153">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="91b02-154">WindowsFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-154">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="91b02-155">WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-155">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="91b02-156">WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-156">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="91b02-157">WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-157">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="91b02-158">WindowsPackageCabResource-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-158">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="91b02-159">WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-159">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="91b02-160">Beroende resurser mellan noder</span><span class="sxs-lookup"><span data-stu-id="91b02-160">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="91b02-161">WaitForAll-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-161">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="91b02-162">WaitForSome-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-162">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="91b02-163">WaitForAny-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-163">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="91b02-164">Paket hanterings resurser</span><span class="sxs-lookup"><span data-stu-id="91b02-164">Package Management resources</span></span>

- [<span data-ttu-id="91b02-165">PackageManagement-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-165">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="91b02-166">PackageManagementSource-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-166">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="91b02-167">Linux-resurser</span><span class="sxs-lookup"><span data-stu-id="91b02-167">Linux resources</span></span>

- [<span data-ttu-id="91b02-168">Linux-Arkiv resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-168">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="91b02-169">Linux-miljö resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-169">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="91b02-170">Linux FileLine-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-170">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="91b02-171">Linux-filresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-171">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="91b02-172">Linux-grupp resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-172">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="91b02-173">Linux-paket resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-173">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="91b02-174">Linux-skript resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-174">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="91b02-175">Linux-Tjänsteresurs</span><span class="sxs-lookup"><span data-stu-id="91b02-175">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="91b02-176">Linux SshAuthorizedKeys-resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-176">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="91b02-177">Linux-användar resurs</span><span class="sxs-lookup"><span data-stu-id="91b02-177">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
