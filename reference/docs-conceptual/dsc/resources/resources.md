---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942155"
---
# <a name="dsc-resources"></a><span data-ttu-id="a5cc7-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="a5cc7-103">DSC Resources</span></span>

><span data-ttu-id="a5cc7-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="a5cc7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a5cc7-105">DSC-resurser (Desired State Configuration) tillhandahåller Bygg stenar för en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="a5cc7-106">En resurs exponerar egenskaper som kan konfigureras (schema) och innehåller PowerShell-skript som de lokala Configuration Manager (LCM) anropar för att göra det.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="a5cc7-107">En resurs kan modellera något som generiskt som en fil eller som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="a5cc7-108">Grupper av resurser som är kombinerade i till en DSC-modul som organiserar alla nödvändiga filer i en struktur som är portabel och innehåller metadata för att identifiera hur resurserna är avsedda att användas.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="a5cc7-109">Varje resurs har ett \*-schema som avgör den syntax som behövs för att använda resursen i en [konfiguration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a5cc7-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="a5cc7-110">En resurs schema kan definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="a5cc7-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="a5cc7-111">**Schema. MOF** -fil: de flesta resurser definierar deras *schema* i en schema. MOF-fil med hjälp av [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="a5cc7-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="a5cc7-112">**"\<resurs namn\>. schema. psm1"** -fil: [sammansatta resurser](../configurations/compositeConfigs.md) definierar deras *schema* i en<ResourceName>. schema. psm1-fil med hjälp av ett [parameter block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="a5cc7-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="a5cc7-113">**"\<resurs namn\>. psm1"** File: Class-based DSC-resurser definierar deras *schema* i klass definitionen.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="a5cc7-114">Objekt betecknas som klass egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="a5cc7-115">Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="a5cc7-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="a5cc7-116">Om du vill hämta syntaxen för en DSC-resurs använder du cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) med parametern `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="a5cc7-117">Den här användningen liknar att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med parametern `-Syntax` för att hämta cmdlet-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="a5cc7-118">De utdata som visas visar den mall som används för ett resurs block för den resurs som du anger.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="a5cc7-119">De utdata du ser liknar utdata nedan, men den här resursens syntax kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="a5cc7-120">Precis som cmdlet-syntaxen är de *nycklar* som visas i hakparenteser valfria.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="a5cc7-121">Typerna anger vilken typ av data varje nyckel förväntar sig.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="a5cc7-122">Nyckeln **säkerställer att** nyckeln är valfri eftersom den används som standard.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="a5cc7-123">I en konfiguration kan ett **tjänst** resurs block se ut så här för att **säkerställa** att Spooler-tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="a5cc7-124">Innan du använder en resurs i en konfiguration måste du importera den med hjälp av [import-dscresource Keyword Supports](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="a5cc7-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="a5cc7-125">Konfigurationer kan innehålla flera instanser av samma resurs typ.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="a5cc7-126">Varje instans måste ha ett unikt namn.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="a5cc7-127">I följande exempel läggs ett andra **tjänst** resurs block till för att konfigurera tjänsten "DHCP".</span><span class="sxs-lookup"><span data-stu-id="a5cc7-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="a5cc7-128">Från och med PowerShell 5,0 lades IntelliSense till för DSC.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="a5cc7-129">Med den här nya funktionen kan du använda \<TABB\> och \<CTRL + blank steg\> för att komplettera nyckel namnen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Slut för ande av resurs flik](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="a5cc7-131">Inbyggda resurser</span><span class="sxs-lookup"><span data-stu-id="a5cc7-131">Built-in resources</span></span>

<span data-ttu-id="a5cc7-132">Förutom community-resurser finns det inbyggda resurser för Windows, resurser för Linux och resurser för över-nod-beroende.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="a5cc7-133">Du kan använda stegen ovan för att fastställa syntaxen för dessa resurser och hur du använder dem.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="a5cc7-134">De sidor som hanterar dessa resurser har arkiverats under **referens**.</span><span class="sxs-lookup"><span data-stu-id="a5cc7-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="a5cc7-135">Inbyggda resurser i Windows</span><span class="sxs-lookup"><span data-stu-id="a5cc7-135">Windows built-in resources</span></span>

* [<span data-ttu-id="a5cc7-136">Arkivera resursen</span><span class="sxs-lookup"><span data-stu-id="a5cc7-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="a5cc7-137">Miljöresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="a5cc7-138">Filresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="a5cc7-139">Gruppresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="a5cc7-140">GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="a5cc7-141">Loggresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="a5cc7-142">Paketresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="a5cc7-143">ProcessSet-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="a5cc7-144">Registerresurser</span><span class="sxs-lookup"><span data-stu-id="a5cc7-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="a5cc7-145">Skriptresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="a5cc7-146">Tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="a5cc7-147">ServiceSet-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="a5cc7-148">Användarresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="a5cc7-149">WindowsFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="a5cc7-150">WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="a5cc7-151">WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="a5cc7-152">WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="a5cc7-153">WindowsPackageCabResource-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="a5cc7-154">WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="a5cc7-155">[Beroende resurser mellan noder](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a5cc7-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="a5cc7-156">WaitForAll-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="a5cc7-157">WaitForSome-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="a5cc7-158">WaitForAny-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="a5cc7-159">Paket hanterings resurser</span><span class="sxs-lookup"><span data-stu-id="a5cc7-159">Package Management resources</span></span>

* [<span data-ttu-id="a5cc7-160">PackageManagement-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="a5cc7-161">PackageManagementSource-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="a5cc7-162">Linux-resurser</span><span class="sxs-lookup"><span data-stu-id="a5cc7-162">Linux resources</span></span>

* [<span data-ttu-id="a5cc7-163">Linux-Arkiv resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="a5cc7-164">Linux-miljö resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="a5cc7-165">Linux FileLine-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="a5cc7-166">Linux-filresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="a5cc7-167">Linux-grupp resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="a5cc7-168">Linux-paket resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="a5cc7-169">Linux-skript resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="a5cc7-170">Linux-Tjänsteresurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="a5cc7-171">Linux SshAuthorizedKeys-resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="a5cc7-172">Linux-användar resurs</span><span class="sxs-lookup"><span data-stu-id="a5cc7-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
