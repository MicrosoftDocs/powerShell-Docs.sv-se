---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046699"
---
# <a name="dsc-resources"></a><span data-ttu-id="b1b72-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="b1b72-103">DSC Resources</span></span>

><span data-ttu-id="b1b72-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b1b72-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b1b72-105">Desired State Configuration (DSC) resurser innehåller byggstenarna för en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b1b72-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="b1b72-106">En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som lokala Configuration Manager (LCM)-anrop till ”gör den det”.</span><span class="sxs-lookup"><span data-stu-id="b1b72-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="b1b72-107">En resurs kan utforma något som allmän som en fil eller så specifik som en inställning för IIS-server.</span><span class="sxs-lookup"><span data-stu-id="b1b72-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="b1b72-108">Grupper av som resurser kombineras till en DSC-modul som organiserar alla filerna som krävs i att en struktur som är portabelt och innehåller metadata för att identifiera hur resurserna är avsedda att användas i.</span><span class="sxs-lookup"><span data-stu-id="b1b72-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="b1b72-109">Varje resurs har en \* schema som anger den syntax som krävs för att använda resursen i en [Configuration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b1b72-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="b1b72-110">Schemat för en resurs kan definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="b1b72-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="b1b72-111">**'Schema.Mof'** fil: De flesta resurser definiera sina *schemat* i en schema.mof fil, använda [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="b1b72-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="b1b72-112">**”\<Resursnamn\>. schema.psm1'** fil: [Sammansatta resurser](../configurations/compositeConfigs.md) definiera sina *schemat* i en ”<ResourceName>. schema.psm1-fil med hjälp av en [Parameterblocket](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="b1b72-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="b1b72-113">**”\<Resursnamn\>.psm1'** fil: Klassen baserat DSC-resurser definiera sina *schemat* i klassdefinitionen.</span><span class="sxs-lookup"><span data-stu-id="b1b72-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="b1b72-114">Syntax objekt betecknas som klassegenskaper.</span><span class="sxs-lookup"><span data-stu-id="b1b72-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="b1b72-115">Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="b1b72-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="b1b72-116">Använd för att hämta syntaxen för en DSC-resurs i [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet med den `-Syntax` parametern.</span><span class="sxs-lookup"><span data-stu-id="b1b72-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="b1b72-117">Den här användningen är ungefär som att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med den `-Syntax` parametern för att hämta cmdlet-syntax.</span><span class="sxs-lookup"><span data-stu-id="b1b72-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="b1b72-118">Du ser utdata visar den mall som användes för en resurs-block för den resurs som du anger.</span><span class="sxs-lookup"><span data-stu-id="b1b72-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="b1b72-119">Du ser utdata bör likna utdata nedan, även om den här resursen syntax kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="b1b72-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="b1b72-120">Som cmdlet-syntax i *nycklar* visas inom hakparentes är valfria.</span><span class="sxs-lookup"><span data-stu-id="b1b72-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="b1b72-121">Typerna ange vilken typ av data som förväntar sig att varje nyckel.</span><span class="sxs-lookup"><span data-stu-id="b1b72-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="b1b72-122">Den **Kontrollera** nyckeln är valfri eftersom standard ”aktuella”.</span><span class="sxs-lookup"><span data-stu-id="b1b72-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="b1b72-123">I en konfiguration för en **Service** resource block kan se ut så här för att **Kontrollera** som tjänsten Spooler körs.</span><span class="sxs-lookup"><span data-stu-id="b1b72-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="b1b72-124">Innan du använder en resurs i en konfiguration, måste du importera den med hjälp av [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="b1b72-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="b1b72-125">Konfigurationer kan innehålla flera instanser av samma resurstypen.</span><span class="sxs-lookup"><span data-stu-id="b1b72-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="b1b72-126">Varje instans måste vara unika namn.</span><span class="sxs-lookup"><span data-stu-id="b1b72-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="b1b72-127">I följande exempel visas en andra **Service** resource block har lagts till för att konfigurera tjänsten ”DHCP”.</span><span class="sxs-lookup"><span data-stu-id="b1b72-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="b1b72-128">Från och med PowerShell 5.0, intellisense lades till för DSC.</span><span class="sxs-lookup"><span data-stu-id="b1b72-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="b1b72-129">Den här nya funktionen kan du använda \<FLIKEN\> och \<Ctrl + blanksteg\> till automatisk komplettering nyckelnamn.</span><span class="sxs-lookup"><span data-stu-id="b1b72-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Tabbifyllning för resursen](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="b1b72-131">Inbyggda resurser</span><span class="sxs-lookup"><span data-stu-id="b1b72-131">Built-in resources</span></span>

<span data-ttu-id="b1b72-132">Förutom community-resurser finns inbyggda resurser för Windows, Linux-resurser och resurser för beroenden mellan noder.</span><span class="sxs-lookup"><span data-stu-id="b1b72-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="b1b72-133">Du kan använda stegen ovan för att fastställa syntaxen för dessa resurser och hur de används.</span><span class="sxs-lookup"><span data-stu-id="b1b72-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="b1b72-134">De sidor som betjänar dessa resurser har arkiverats **referens**.</span><span class="sxs-lookup"><span data-stu-id="b1b72-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="b1b72-135">Inbyggda resurser för Windows</span><span class="sxs-lookup"><span data-stu-id="b1b72-135">Windows built-in resources</span></span>

* [<span data-ttu-id="b1b72-136">Arkivera resursen</span><span class="sxs-lookup"><span data-stu-id="b1b72-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="b1b72-137">Miljöresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="b1b72-138">Filresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="b1b72-139">Gruppresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="b1b72-140">GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="b1b72-141">Loggresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="b1b72-142">Paketresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="b1b72-143">ProcessSet-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="b1b72-144">Registerresurser</span><span class="sxs-lookup"><span data-stu-id="b1b72-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="b1b72-145">Skriptresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="b1b72-146">Tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="b1b72-147">ServiceSet-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="b1b72-148">Användarresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="b1b72-149">WindowsFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="b1b72-150">WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="b1b72-151">WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="b1b72-152">WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="b1b72-153">WindowsPackageCabResource resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="b1b72-154">WindowsProcess-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="b1b72-155">[Mellan noder beroende](../configurations/crossNodeDependencies.md) resurser</span><span class="sxs-lookup"><span data-stu-id="b1b72-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="b1b72-156">WaitForAll resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="b1b72-157">WaitForSome resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="b1b72-158">WaitForAny resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="b1b72-159">Paketet Management-resurser</span><span class="sxs-lookup"><span data-stu-id="b1b72-159">Package Management resources</span></span>

* [<span data-ttu-id="b1b72-160">PackageManagement-resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="b1b72-161">PackageManagementSource resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="b1b72-162">Linux-resurser</span><span class="sxs-lookup"><span data-stu-id="b1b72-162">Linux resources</span></span>

* [<span data-ttu-id="b1b72-163">Linux Arkivera resursen</span><span class="sxs-lookup"><span data-stu-id="b1b72-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="b1b72-164">Miljöresurs för Linux</span><span class="sxs-lookup"><span data-stu-id="b1b72-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="b1b72-165">Linux FileLine resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="b1b72-166">Linux-filresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="b1b72-167">Linux Gruppresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="b1b72-168">Linux Paketresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="b1b72-169">Skriptresurs på Linux</span><span class="sxs-lookup"><span data-stu-id="b1b72-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="b1b72-170">Linux-tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="b1b72-171">Linux SshAuthorizedKeys resurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="b1b72-172">Linux användarresurs</span><span class="sxs-lookup"><span data-stu-id="b1b72-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
