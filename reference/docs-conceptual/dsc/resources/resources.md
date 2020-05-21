---
ms.date: 02/28/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: bae08447763a3bdb6ee8fcdd4f8d49209a5de805
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692197"
---
# <a name="dsc-resources"></a><span data-ttu-id="eabbd-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="eabbd-103">DSC Resources</span></span>

> <span data-ttu-id="eabbd-104">Gäller för Windows PowerShell 4,0 och uppåt.</span><span class="sxs-lookup"><span data-stu-id="eabbd-104">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="eabbd-105">Översikt</span><span class="sxs-lookup"><span data-stu-id="eabbd-105">Overview</span></span>

<span data-ttu-id="eabbd-106">DSC-resurser (Desired State Configuration) tillhandahåller Bygg stenar för en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="eabbd-106">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="eabbd-107">En resurs exponerar egenskaper som kan konfigureras (schema) och innehåller PowerShell-skript som de lokala Configuration Manager (LCM) anropar för att göra det.</span><span class="sxs-lookup"><span data-stu-id="eabbd-107">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="eabbd-108">En resurs kan modellera något som generiskt som en fil eller som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="eabbd-108">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="eabbd-109">Grupper av resurser som är kombinerade i till en DSC-modul som organiserar alla nödvändiga filer i en struktur som är portabel och innehåller metadata för att identifiera hur resurserna är avsedda att användas.</span><span class="sxs-lookup"><span data-stu-id="eabbd-109">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="eabbd-110">Varje resurs har ett \*-schema som avgör den syntax som behövs för att använda resursen i en [konfiguration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="eabbd-110">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span>
<span data-ttu-id="eabbd-111">En resurs schema kan definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="eabbd-111">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="eabbd-112">`Schema.Mof`fil: de flesta resurser definierar _schemat_ i en ' schema. MOF '-fil med hjälp av [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="eabbd-112">`Schema.Mof` file: Most resources define their _schema_ in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="eabbd-113">`<Resource Name>.schema.psm1`fil: [sammansatta resurser](../configurations/compositeConfigs.md) definierar deras *schema* i en `<ResourceName>.schema.psm1` fil med hjälp av ett [parameter block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="eabbd-113">`<Resource Name>.schema.psm1` file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a `<ResourceName>.schema.psm1` file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="eabbd-114">`<Resource Name>.psm1`fil: klassbaserade DSC-resurser definierar deras _schema_ i klass definitionen.</span><span class="sxs-lookup"><span data-stu-id="eabbd-114">`<Resource Name>.psm1` file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="eabbd-115">Objekt betecknas som klass egenskaper.</span><span class="sxs-lookup"><span data-stu-id="eabbd-115">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="eabbd-116">Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="eabbd-116">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="eabbd-117">Om du vill hämta syntaxen för en DSC-resurs använder du cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) med `-Syntax` parametern.</span><span class="sxs-lookup"><span data-stu-id="eabbd-117">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="eabbd-118">Den här användningen liknar att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med `-Syntax` parametern för att hämta cmdlet-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="eabbd-118">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="eabbd-119">De utdata som visas visar den mall som används för ett resurs block för den resurs som du anger.</span><span class="sxs-lookup"><span data-stu-id="eabbd-119">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="eabbd-120">De utdata du ser liknar utdata nedan, men den här resursens syntax kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="eabbd-120">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="eabbd-121">Precis som cmdlet-syntaxen är de _nycklar_ som visas i hakparenteser valfria.</span><span class="sxs-lookup"><span data-stu-id="eabbd-121">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="eabbd-122">Typerna anger vilken typ av data varje nyckel förväntar sig.</span><span class="sxs-lookup"><span data-stu-id="eabbd-122">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="eabbd-123">Nyckeln **säkerställer att** nyckeln är valfri eftersom den används som standard.</span><span class="sxs-lookup"><span data-stu-id="eabbd-123">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="eabbd-124">I en konfiguration kan ett **tjänst** resurs block se ut så här för att **säkerställa** att Spooler-tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="eabbd-124">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="eabbd-125">Innan du använder en resurs i en konfiguration måste du importera den med hjälp av [import-dscresource Keyword Supports](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="eabbd-125">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="eabbd-126">Konfigurationer kan innehålla flera instanser av samma resurs typ.</span><span class="sxs-lookup"><span data-stu-id="eabbd-126">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="eabbd-127">Varje instans måste ha ett unikt namn.</span><span class="sxs-lookup"><span data-stu-id="eabbd-127">Each instance must be uniquely named.</span></span> <span data-ttu-id="eabbd-128">I följande exempel läggs ett andra **tjänst** resurs block till för att konfigurera tjänsten "DHCP".</span><span class="sxs-lookup"><span data-stu-id="eabbd-128">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="eabbd-129">Från och med PowerShell 5,0 lades IntelliSense till för DSC.</span><span class="sxs-lookup"><span data-stu-id="eabbd-129">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="eabbd-130">Med den här nya funktionen kan du <kbd>TAB</kbd> använda TABB <kbd>-och</kbd> + <kbd>rymd utrymme</kbd> för att komplettera nyckel namn automatiskt.</span><span class="sxs-lookup"><span data-stu-id="eabbd-130">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![Slut för ande av resurs flik](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="eabbd-132">Typer av resurser</span><span class="sxs-lookup"><span data-stu-id="eabbd-132">Types of resources</span></span>

<span data-ttu-id="eabbd-133">Windows levereras med inbyggda resurser och Linux har leverantörsspecifika resurser.</span><span class="sxs-lookup"><span data-stu-id="eabbd-133">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="eabbd-134">Det finns resurser för [över-nod-beroenden](../configurations/crossNodeDependencies.md), paket hanterings resurser samt[ägda och bevarade resurser](https://github.com/dsccommunity).</span><span class="sxs-lookup"><span data-stu-id="eabbd-134">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="eabbd-135">Du kan använda ovanstående steg för att fastställa syntaxen för dessa resurser och hur du använder dem.</span><span class="sxs-lookup"><span data-stu-id="eabbd-135">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="eabbd-136">De sidor som hanterar dessa resurser har arkiverats under **referens**.</span><span class="sxs-lookup"><span data-stu-id="eabbd-136">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="eabbd-137">Inbyggda resurser i Windows</span><span class="sxs-lookup"><span data-stu-id="eabbd-137">Windows built-in resources</span></span>

- [<span data-ttu-id="eabbd-138">Arkivera resursen</span><span class="sxs-lookup"><span data-stu-id="eabbd-138">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="eabbd-139">Miljöresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-139">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="eabbd-140">Filresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-140">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="eabbd-141">Gruppresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-141">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="eabbd-142">GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-142">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="eabbd-143">Loggresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-143">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="eabbd-144">Paketresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-144">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="eabbd-145">ProcessSet-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-145">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="eabbd-146">Registerresurser</span><span class="sxs-lookup"><span data-stu-id="eabbd-146">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="eabbd-147">Skriptresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-147">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="eabbd-148">Tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-148">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="eabbd-149">ServiceSet-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-149">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="eabbd-150">Användarresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-150">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="eabbd-151">WindowsFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-151">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="eabbd-152">WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-152">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="eabbd-153">WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-153">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="eabbd-154">WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-154">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="eabbd-155">WindowsPackageCabResource-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-155">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="eabbd-156">WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-156">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="eabbd-157">Beroende resurser mellan noder</span><span class="sxs-lookup"><span data-stu-id="eabbd-157">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="eabbd-158">WaitForAll-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-158">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="eabbd-159">WaitForSome-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-159">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="eabbd-160">WaitForAny-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-160">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="eabbd-161">Paket hanterings resurser</span><span class="sxs-lookup"><span data-stu-id="eabbd-161">Package Management resources</span></span>

- [<span data-ttu-id="eabbd-162">PackageManagement-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-162">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="eabbd-163">PackageManagementSource-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-163">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="eabbd-164">Linux-resurser</span><span class="sxs-lookup"><span data-stu-id="eabbd-164">Linux resources</span></span>

- [<span data-ttu-id="eabbd-165">Linux-Arkiv resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-165">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="eabbd-166">Linux-miljö resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-166">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="eabbd-167">Linux FileLine-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-167">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="eabbd-168">Linux-filresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-168">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="eabbd-169">Linux-grupp resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-169">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="eabbd-170">Linux-paket resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-170">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="eabbd-171">Linux-skript resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-171">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="eabbd-172">Linux-Tjänsteresurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-172">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="eabbd-173">Linux SshAuthorizedKeys-resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-173">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="eabbd-174">Linux-användar resurs</span><span class="sxs-lookup"><span data-stu-id="eabbd-174">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
