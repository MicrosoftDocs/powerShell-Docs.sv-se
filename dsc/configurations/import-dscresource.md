---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Import-DSCResource
ms.openlocfilehash: 735b2c2b4ae5101ded333768f00b46cb54d541b0
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323020"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="33a6a-103">Använda Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="33a6a-103">Using Import-DSCResource</span></span>

<span data-ttu-id="33a6a-104">`Import-DScResource`är ett dynamiskt nyckelord som bara kan användas i ett konfigurations skript block.</span><span class="sxs-lookup"><span data-stu-id="33a6a-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="33a6a-105">`Import-DSCResource` Nyckelordet för att importera de resurser som behövs i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="33a6a-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="33a6a-106">Resurser under `$pshome` importeras automatiskt, men det anses fortfarande vara bästa praxis att importera alla resurser som används i [konfigurationen](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="33a6a-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="33a6a-107">Syntaxen för `Import-DSCResource` visas nedan.</span><span class="sxs-lookup"><span data-stu-id="33a6a-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="33a6a-108">När du anger moduler efter namn är det ett krav för att lista var och en på en ny rad.</span><span class="sxs-lookup"><span data-stu-id="33a6a-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="33a6a-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="33a6a-109">Parameter</span></span>  |<span data-ttu-id="33a6a-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33a6a-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="33a6a-111">DSC-resursens namn som du måste importera.</span><span class="sxs-lookup"><span data-stu-id="33a6a-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="33a6a-112">Om modulnamnet anges söker kommandot efter dessa DSC-resurser i den här modulen. Annars söker kommandot igenom DSC-resurserna i alla DSC-resurs Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="33a6a-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="33a6a-113">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="33a6a-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="33a6a-114">Modulens namn eller modulens specifikation.</span><span class="sxs-lookup"><span data-stu-id="33a6a-114">The module name, or module specification.</span></span>  <span data-ttu-id="33a6a-115">Om du anger vilka resurser som ska importeras från en modul försöker kommandot endast importera resurserna.</span><span class="sxs-lookup"><span data-stu-id="33a6a-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="33a6a-116">Om du bara anger modulen importeras alla DSC-resurser i modulen.</span><span class="sxs-lookup"><span data-stu-id="33a6a-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="33a6a-117">Exempel: Använd import-Dscresource Keyword Supports i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="33a6a-117">Example: Use Import-DSCResource within a configuration</span></span>

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
> <span data-ttu-id="33a6a-118">Det finns inte stöd för att ange flera värden för resurs namn och moduler i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="33a6a-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="33a6a-119">Det kan ha icke-deterministiskt beteende för vilken resurs som ska läsas in från vilken modul i samma resurs som finns i flera moduler.</span><span class="sxs-lookup"><span data-stu-id="33a6a-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="33a6a-120">Kommandot nedan leder till ett fel under kompileringen.</span><span class="sxs-lookup"><span data-stu-id="33a6a-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="33a6a-121">Saker att tänka på när du bara använder parametern name:</span><span class="sxs-lookup"><span data-stu-id="33a6a-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="33a6a-122">Det är en resurs intensiv åtgärd beroende på hur många moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="33a6a-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="33a6a-123">Den första resursen som påträffas med det aktuella namnet läses in.</span><span class="sxs-lookup"><span data-stu-id="33a6a-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="33a6a-124">Om det finns fler än en resurs med samma namn installerat kan fel resurs läsas in.</span><span class="sxs-lookup"><span data-stu-id="33a6a-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="33a6a-125">Den rekommenderade användningen är att ange `–ModuleName` `-Name` med parametern, enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="33a6a-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="33a6a-126">Den här användningen har följande fördelar:</span><span class="sxs-lookup"><span data-stu-id="33a6a-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="33a6a-127">Det minskar prestanda påverkan genom att begränsa Sök omfånget för den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="33a6a-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="33a6a-128">Det definierar uttryckligen den modul som definierar resursen, vilket säkerställer att rätt resurs läses in.</span><span class="sxs-lookup"><span data-stu-id="33a6a-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="33a6a-129">I PowerShell 5,0 kan DSC-resurser ha flera versioner och versioner kan installeras på en dator sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="33a6a-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="33a6a-130">Detta implementeras genom att ha flera versioner av en resurs-modul som finns i samma modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="33a6a-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="33a6a-131">Mer information finns i [använda resurser med flera versioner](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="33a6a-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="33a6a-132">IntelliSense med import-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="33a6a-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="33a6a-133">När du redigerar DSC-konfigurationen i ISE tillhandahåller PowerShell IntelliSence för resurser och resurs egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33a6a-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="33a6a-134">Resurs definitioner under `$pshome` modulens sökväg läses in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="33a6a-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="33a6a-135">När du importerar resurser med hjälp `Import-DSCResource` av nyckelordet läggs de angivna resurs definitionerna till och IntelliSense expanderas för att inkludera den importerade resursens schema.</span><span class="sxs-lookup"><span data-stu-id="33a6a-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Resurs-IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="33a6a-137">Från och med PowerShell 5,0 har TABB-slutförande lagts till i ISE för DSC-resurser och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="33a6a-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="33a6a-138">Mer information finns i [resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="33a6a-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="33a6a-139">När du kompilerar konfigurationen använder PowerShell de importerade resurs definitionerna för att verifiera alla resurs block i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="33a6a-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="33a6a-140">Varje resurs block verifieras med hjälp av resursens schema definition, för följande regler.</span><span class="sxs-lookup"><span data-stu-id="33a6a-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="33a6a-141">Endast egenskaper som definieras i schemat används.</span><span class="sxs-lookup"><span data-stu-id="33a6a-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="33a6a-142">Data typerna för varje egenskap är korrekta.</span><span class="sxs-lookup"><span data-stu-id="33a6a-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="33a6a-143">Nycklar egenskaper har angetts.</span><span class="sxs-lookup"><span data-stu-id="33a6a-143">Keys properties are specified.</span></span>
- <span data-ttu-id="33a6a-144">Ingen skrivskyddad egenskap används.</span><span class="sxs-lookup"><span data-stu-id="33a6a-144">No read-only property is used.</span></span>
- <span data-ttu-id="33a6a-145">Validering av värde mappnings typer.</span><span class="sxs-lookup"><span data-stu-id="33a6a-145">Validation on value maps types.</span></span>

<span data-ttu-id="33a6a-146">Överväg följande konfiguration:</span><span class="sxs-lookup"><span data-stu-id="33a6a-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="33a6a-147">Att kompilera den här konfigurationen resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="33a6a-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="33a6a-148">Med IntelliSense och schema validering kan du fånga fler fel under parsning och kompilering, vilket undviker komplikationer vid körnings tillfället.</span><span class="sxs-lookup"><span data-stu-id="33a6a-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="33a6a-149">Varje DSC-resurs kan ha ett namn och ett **FriendlyName** som definieras av resursens schema.</span><span class="sxs-lookup"><span data-stu-id="33a6a-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="33a6a-150">Nedan visas de två första raderna i "MSFT_ServiceResource. Shema. MOF".</span><span class="sxs-lookup"><span data-stu-id="33a6a-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="33a6a-151">När du använder den här resursen i en konfiguration kan du ange **MSFT_ServiceResource** eller **tjänst**.</span><span class="sxs-lookup"><span data-stu-id="33a6a-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="33a6a-152">Skillnader mellan PowerShell v4 och v5</span><span class="sxs-lookup"><span data-stu-id="33a6a-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="33a6a-153">Det finns flera skillnader som du ser när du redigerar konfigurationer i PowerShell 4,0 jämfört med PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="33a6a-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="33a6a-154">Det här avsnittet visar skillnaderna som du ser relevanta för den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="33a6a-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="33a6a-155">Flera resurs versioner</span><span class="sxs-lookup"><span data-stu-id="33a6a-155">Multiple Resource Versions</span></span>

<span data-ttu-id="33a6a-156">Det finns inte stöd för att installera och använda flera versioner av resurser sida vid sida i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="33a6a-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="33a6a-157">Om du upptäcker problem med att importera resurser till din konfiguration måste du kontrol lera att du bara har en version av resursen installerad.</span><span class="sxs-lookup"><span data-stu-id="33a6a-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="33a6a-158">I bilden nedan installeras två versioner av **xPSDesiredStateConfiguration** -modulen.</span><span class="sxs-lookup"><span data-stu-id="33a6a-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Flera resurs versioner har åtgärd ATS](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="33a6a-160">Kopiera innehållet i den önskade modulens version till den översta nivån i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="33a6a-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Flera resurs versioner har åtgärd ATS](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="33a6a-162">Resurs plats</span><span class="sxs-lookup"><span data-stu-id="33a6a-162">Resource location</span></span>

<span data-ttu-id="33a6a-163">När du redigerar och kompilerar konfigurationer kan dina resurser lagras i valfri katalog som anges av din [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="33a6a-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="33a6a-164">I PowerShell 4,0 kräver LCM att alla DSC-resurspooler lagras under "program Files\WindowsPowerShell\Modules" eller `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="33a6a-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="33a6a-165">Från och med PowerShell 5,0 togs detta krav bort och resurspooler kan lagras i valfri katalog som anges av `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="33a6a-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="33a6a-166">Se även</span><span class="sxs-lookup"><span data-stu-id="33a6a-166">See also</span></span>

- [<span data-ttu-id="33a6a-167">Resurser</span><span class="sxs-lookup"><span data-stu-id="33a6a-167">Resources</span></span>](../resources/resources.md)
