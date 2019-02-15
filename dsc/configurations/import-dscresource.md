---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Använda Import-DSCResource
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265509"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="48730-103">Använda Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="48730-103">Using Import-DSCResource</span></span>

<span data-ttu-id="48730-104">`Import-DScResource` är ett dynamiskt nyckelord som kan bara användas i ett skriptblock konfiguration.</span><span class="sxs-lookup"><span data-stu-id="48730-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="48730-105">Den `Import-DSCResource` nyckelord för att importera alla resurser som behövs i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="48730-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="48730-106">Resurser under `$phsome` importeras automatiskt, men den betraktas ändå bäst att explicit importera alla resurser som används i din [Configuration](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="48730-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="48730-107">Syntaxen för `Import-DSCResource` visas nedan.</span><span class="sxs-lookup"><span data-stu-id="48730-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="48730-108">När du anger moduler efter namn, är det ett krav att visa på en ny rad.</span><span class="sxs-lookup"><span data-stu-id="48730-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="48730-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="48730-109">Parameter</span></span>  |<span data-ttu-id="48730-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="48730-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="48730-111">Namn för DSC-resurs som du måste importera.</span><span class="sxs-lookup"><span data-stu-id="48730-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="48730-112">Om modulnamnet anges söker kommandot efter dessa DSC-resurser i den här modulen. kommandot söker annars DSC-resurser i alla sökvägar för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="48730-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="48730-113">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="48730-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="48730-114">Modulnamn eller module-specifikationen.</span><span class="sxs-lookup"><span data-stu-id="48730-114">The module name, or module specification.</span></span>  <span data-ttu-id="48730-115">Om du anger resurser som ska importeras från en modul görs kommandot försök att importera endast de resurserna.</span><span class="sxs-lookup"><span data-stu-id="48730-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="48730-116">Om du anger modulen endast importerar kommandot alla DSC-resurser i modulen.</span><span class="sxs-lookup"><span data-stu-id="48730-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="48730-117">Exempel: Använda importera DSCResource i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="48730-117">Example: Use Import-DSCResource within a configuration</span></span>

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="48730-118">Att ange flera värden för namn på resursen och moduler i samma kommando stöds inte.</span><span class="sxs-lookup"><span data-stu-id="48730-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="48730-119">Den kan ha icke-deterministiska beteende om vilken resurs som ska läsas in från vilken modul samma resurs finns i flera moduler.</span><span class="sxs-lookup"><span data-stu-id="48730-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="48730-120">Under kommandot resulterar i fel under kompilering.</span><span class="sxs-lookup"><span data-stu-id="48730-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="48730-121">Saker att tänka på när du använder bara parametern Name:</span><span class="sxs-lookup"><span data-stu-id="48730-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="48730-122">Det är en resursintensiv åtgärd beroende på antalet moduler som installerats på datorn.</span><span class="sxs-lookup"><span data-stu-id="48730-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="48730-123">Den kommer att läsa in den första resursen med det namnet hittades.</span><span class="sxs-lookup"><span data-stu-id="48730-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="48730-124">I fall där det finns fler än en resurs med samma namn som har installerats, det gick att läsa in fel resurs.</span><span class="sxs-lookup"><span data-stu-id="48730-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="48730-125">Den rekommenderade användningen är att ange `–ModuleName` med den `-Name` parametern, som beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="48730-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="48730-126">Denna användning har följande fördelar:</span><span class="sxs-lookup"><span data-stu-id="48730-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="48730-127">Det minskar påverkan på prestandan genom att begränsa omfattningen av sökningen för den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="48730-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="48730-128">Den definierar uttryckligen modulen definiera resursen, se till att rätt resurs har lästs in.</span><span class="sxs-lookup"><span data-stu-id="48730-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="48730-129">I PowerShell 5.0 DSC-resurser kan ha flera versioner och versioner kan installeras på en dator sida-vid-sida.</span><span class="sxs-lookup"><span data-stu-id="48730-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="48730-130">Det har implementerats genom att låta flera versioner av en Resursmodul som ingår i samma modul mapp.</span><span class="sxs-lookup"><span data-stu-id="48730-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="48730-131">Mer information finns i [av resurser med flera versioner](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="48730-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="48730-132">IntelliSense med Import DSCResource</span><span class="sxs-lookup"><span data-stu-id="48730-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="48730-133">När du redigerar DSC-konfigurationen i ISE innehåller PowerShell IntelliSence för resurser och resursegenskaper.</span><span class="sxs-lookup"><span data-stu-id="48730-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="48730-134">Resursdefinitionerna under den `$pshome` sökvägen modulen laddas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="48730-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="48730-135">När du importerar resurser med hjälp av den `Import-DSCResource` nyckelordet angivna resursdefinitionerna läggs och Intellisense utökas för att inkludera resursen importerade schemat.</span><span class="sxs-lookup"><span data-stu-id="48730-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Resursen Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="48730-137">Från och med PowerShell 5.0, har flikavslutande lagts till ISE för DSC-resurser och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="48730-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="48730-138">Mer information finns i [resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="48730-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="48730-139">Vid kompilering av konfigurationen, använder PowerShell importerade resursdefinitionerna för att verifiera alla resurs block i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="48730-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="48730-140">Varje resurs block verifieras med hjälp av resursens schemadefinition för följande regler.</span><span class="sxs-lookup"><span data-stu-id="48730-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="48730-141">Endast egenskaper som definierats i schemat används.</span><span class="sxs-lookup"><span data-stu-id="48730-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="48730-142">Datatyper av för varje egenskap är korrekta.</span><span class="sxs-lookup"><span data-stu-id="48730-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="48730-143">Nycklar egenskaper har angetts.</span><span class="sxs-lookup"><span data-stu-id="48730-143">Keys properties are specified.</span></span>
- <span data-ttu-id="48730-144">Ingen skrivskyddad egenskap används.</span><span class="sxs-lookup"><span data-stu-id="48730-144">No read-only property is used.</span></span>
- <span data-ttu-id="48730-145">Validering av värdet mappar typer.</span><span class="sxs-lookup"><span data-stu-id="48730-145">Validation on value maps types.</span></span>

<span data-ttu-id="48730-146">Överväg följande konfiguration:</span><span class="sxs-lookup"><span data-stu-id="48730-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="48730-147">Kompilerar den här konfigurationen leder till att ett fel.</span><span class="sxs-lookup"><span data-stu-id="48730-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="48730-148">Verifiering av IntelliSense och schemat kan du fånga upp mer fel under parse och sammanställning tid att undvika problem vid körning.</span><span class="sxs-lookup"><span data-stu-id="48730-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="48730-149">Varje DSC-resurs kan ha ett namn och en **FriendlyName** definieras av resursens schema.</span><span class="sxs-lookup"><span data-stu-id="48730-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="48730-150">Nedan visas de två första raderna i ”MSFT_ServiceResource.shema.mof”.</span><span class="sxs-lookup"><span data-stu-id="48730-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="48730-151">När du använder den här resursen i en konfiguration, kan du ange **MSFT_ServiceResource** eller **tjänsten**.</span><span class="sxs-lookup"><span data-stu-id="48730-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="48730-152">PowerShell v4 och v5 skillnader</span><span class="sxs-lookup"><span data-stu-id="48730-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="48730-153">Det finns flera skillnader som du kan se när redigering konfigurationer i jämfört med PowerShell 4.0. PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="48730-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="48730-154">Det här avsnittet kommer Markera skillnaderna som visas är relevanta för den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="48730-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="48730-155">Flera resurs-versioner</span><span class="sxs-lookup"><span data-stu-id="48730-155">Multiple Resource Versions</span></span>

<span data-ttu-id="48730-156">Installera och använda flera versioner av resurser sida vid sida stöds inte i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="48730-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="48730-157">Se till att du bara har en version av resursen installeras om du upptäcker problem importerar resurser till din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="48730-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="48730-158">I bilden nedan, två versioner av den **xPSDesiredStateConfiguration** modulen är installerad.</span><span class="sxs-lookup"><span data-stu-id="48730-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Flera resurs versioner fast](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="48730-160">Kopiera innehållet i din önskade Modulversion till den översta nivån i modul-katalog.</span><span class="sxs-lookup"><span data-stu-id="48730-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Flera resurs versioner fast](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="48730-162">Resursplats</span><span class="sxs-lookup"><span data-stu-id="48730-162">Resource location</span></span>

<span data-ttu-id="48730-163">När redigering och sammanställa konfigurationer, dina resurser kan lagras i katalogen som anges av din [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="48730-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="48730-164">PowerShell 4.0 i MGM kräver att alla DSC resurs moduler lagras under ”programmet Files\WindowsPowerShell\Modules” eller `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="48730-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="48730-165">Från och med PowerShell 5.0 kan det här kravet togs bort och resursen moduler kan lagras i katalogen som anges av `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="48730-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="48730-166">Se även</span><span class="sxs-lookup"><span data-stu-id="48730-166">See also</span></span>

- [<span data-ttu-id="48730-167">Resurser</span><span class="sxs-lookup"><span data-stu-id="48730-167">Resources</span></span>](../resources/resources.md)
