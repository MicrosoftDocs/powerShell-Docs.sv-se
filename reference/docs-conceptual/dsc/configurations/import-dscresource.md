---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Import-DSCResource
description: Import-DSCResource är ett dynamiskt nyckelord som bara kan användas i ett konfigurations skript block. Den används för att importera de resurspooler som behövs i konfigurationen.
ms.openlocfilehash: f6dcad2c56848ec25eb79332c96fe6b0d438fe95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658511"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="de739-105">Använda Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="de739-105">Using Import-DSCResource</span></span>

<span data-ttu-id="de739-106">`Import-DSCResource` är ett dynamiskt nyckelord som bara kan användas i ett konfigurations skript block för att importera de resurser som behövs i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="de739-106">`Import-DSCResource` is a dynamic keyword, which can only be used inside a Configuration script block to import any resources needed in your Configuration.</span></span> <span data-ttu-id="de739-107">Resurser under `$PSHOME` importeras automatiskt, men det anses fortfarande vara bästa praxis att importera alla resurser som används i [konfigurationen](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="de739-107">Resources under `$PSHOME` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="de739-108">Syntaxen för `Import-DSCResource` visas nedan.</span><span class="sxs-lookup"><span data-stu-id="de739-108">The syntax for `Import-DSCResource` is shown below.</span></span> <span data-ttu-id="de739-109">När du anger moduler efter namn är det ett krav för att lista var och en på en ny rad.</span><span class="sxs-lookup"><span data-stu-id="de739-109">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|    <span data-ttu-id="de739-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="de739-110">Parameter</span></span>     |                                                                                                                      <span data-ttu-id="de739-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="de739-111">Description</span></span>                                                                                                                      |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-Name`          | <span data-ttu-id="de739-112">DSC-resursens namn som du måste importera.</span><span class="sxs-lookup"><span data-stu-id="de739-112">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="de739-113">Om modulnamnet anges söker kommandot efter dessa DSC-resurser i den här modulen. Annars söker kommandot igenom DSC-resurserna i alla DSC-resurs Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="de739-113">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="de739-114">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="de739-114">Wildcards are supported.</span></span> |
| `-ModuleName`    | <span data-ttu-id="de739-115">Modulens namn eller modulens specifikation.</span><span class="sxs-lookup"><span data-stu-id="de739-115">The module name, or module specification.</span></span>  <span data-ttu-id="de739-116">Om du anger vilka resurser som ska importeras från en modul försöker kommandot endast importera resurserna.</span><span class="sxs-lookup"><span data-stu-id="de739-116">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="de739-117">Om du bara anger modulen importeras alla DSC-resurser i modulen.</span><span class="sxs-lookup"><span data-stu-id="de739-117">If you specify the module only, the command imports all the DSC resources in the module.</span></span>            |
| `-ModuleVersion` | <span data-ttu-id="de739-118">Från och med PowerShell 5,0 kan du ange vilken version av en modul som en konfiguration ska använda.</span><span class="sxs-lookup"><span data-stu-id="de739-118">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="de739-119">Mer information finns i [Importera en angiven version av en installerad resurs](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="de739-119">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>                                                    |

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="de739-120">Exempel: använda Import-DSCResource i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="de739-120">Example: Use Import-DSCResource within a configuration</span></span>

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
> <span data-ttu-id="de739-121">Det finns inte stöd för att ange flera värden för resurs namn och moduler i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="de739-121">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span>
> <span data-ttu-id="de739-122">Det kan ha icke-deterministiskt beteende för vilken resurs som ska läsas in från vilken modul i samma resurs som finns i flera moduler.</span><span class="sxs-lookup"><span data-stu-id="de739-122">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="de739-123">Kommandot nedan leder till ett fel under kompileringen.</span><span class="sxs-lookup"><span data-stu-id="de739-123">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="de739-124">Saker att tänka på när du bara använder parametern name:</span><span class="sxs-lookup"><span data-stu-id="de739-124">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="de739-125">Det är en resurs intensiv åtgärd beroende på hur många moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="de739-125">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="de739-126">Den första resursen som påträffas med det aktuella namnet läses in.</span><span class="sxs-lookup"><span data-stu-id="de739-126">It will load the first resource found with the given name.</span></span> <span data-ttu-id="de739-127">Om det finns fler än en resurs med samma namn installerat kan fel resurs läsas in.</span><span class="sxs-lookup"><span data-stu-id="de739-127">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="de739-128">Den rekommenderade användningen är att ange `–ModuleName` med `-Name` parametern, enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="de739-128">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="de739-129">Den här användningen har följande fördelar:</span><span class="sxs-lookup"><span data-stu-id="de739-129">This usage has the following benefits:</span></span>

- <span data-ttu-id="de739-130">Det minskar prestanda påverkan genom att begränsa Sök omfånget för den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="de739-130">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="de739-131">Det definierar uttryckligen den modul som definierar resursen, vilket säkerställer att rätt resurs läses in.</span><span class="sxs-lookup"><span data-stu-id="de739-131">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="de739-132">I PowerShell 5,0 kan DSC-resurser ha flera versioner och versioner kan installeras på en dator sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="de739-132">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="de739-133">Detta implementeras genom att ha flera versioner av en resurs-modul som finns i samma modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="de739-133">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span> <span data-ttu-id="de739-134">Mer information finns i [använda resurser med flera versioner](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="de739-134">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="de739-135">IntelliSense med Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="de739-135">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="de739-136">När du redigerar DSC-konfigurationen i ISE tillhandahåller PowerShell IntelliSence för resurser och resurs egenskaper.</span><span class="sxs-lookup"><span data-stu-id="de739-136">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="de739-137">Resurs definitioner under `$pshome` modulens sökväg läses in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="de739-137">Resource definitions under the `$pshome` module path are loaded automatically.</span></span>
<span data-ttu-id="de739-138">När du importerar resurser med hjälp av `Import-DSCResource` nyckelordet läggs de angivna resurs definitionerna till och IntelliSense expanderas för att inkludera den importerade resursens schema.</span><span class="sxs-lookup"><span data-stu-id="de739-138">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![IntelliSense i ISE för en DSC-resurs](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="de739-140">Från och med PowerShell 5,0 har TABB-slutförande lagts till i ISE för DSC-resurser och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="de739-140">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="de739-141">Mer information finns i [resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="de739-141">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="de739-142">När du kompilerar konfigurationen använder PowerShell de importerade resurs definitionerna för att verifiera alla resurs block i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="de739-142">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span> <span data-ttu-id="de739-143">Varje resurs block verifieras med hjälp av resursens schema definition, för följande regler.</span><span class="sxs-lookup"><span data-stu-id="de739-143">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="de739-144">Endast egenskaper som definieras i schemat används.</span><span class="sxs-lookup"><span data-stu-id="de739-144">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="de739-145">Data typerna för varje egenskap är korrekta.</span><span class="sxs-lookup"><span data-stu-id="de739-145">The data types for each property are correct.</span></span>
- <span data-ttu-id="de739-146">Nycklar egenskaper har angetts.</span><span class="sxs-lookup"><span data-stu-id="de739-146">Keys properties are specified.</span></span>
- <span data-ttu-id="de739-147">Ingen skrivskyddad egenskap används.</span><span class="sxs-lookup"><span data-stu-id="de739-147">No read-only property is used.</span></span>
- <span data-ttu-id="de739-148">Validering av värde mappnings typer.</span><span class="sxs-lookup"><span data-stu-id="de739-148">Validation on value maps types.</span></span>

<span data-ttu-id="de739-149">Överväg följande konfiguration:</span><span class="sxs-lookup"><span data-stu-id="de739-149">Consider the following configuration:</span></span>

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

<span data-ttu-id="de739-150">Att kompilera den här konfigurationen resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="de739-150">Compiling this Configuration results in an error.</span></span>

```Output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or
valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values:
Present, Absent.
```

<span data-ttu-id="de739-151">Med IntelliSense och schema validering kan du fånga fler fel under parsning och kompilering, vilket undviker komplikationer vid körnings tillfället.</span><span class="sxs-lookup"><span data-stu-id="de739-151">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="de739-152">Varje DSC-resurs kan ha ett namn och ett **FriendlyName** som definieras av resursens schema.</span><span class="sxs-lookup"><span data-stu-id="de739-152">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="de739-153">Nedan visas de två första raderna i "MSFT_ServiceResource. Shema. MOF".</span><span class="sxs-lookup"><span data-stu-id="de739-153">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
>
> <span data-ttu-id="de739-154">När du använder den här resursen i en konfiguration kan du ange **MSFT_ServiceResource** eller **tjänst** .</span><span class="sxs-lookup"><span data-stu-id="de739-154">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service** .</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="de739-155">Skillnader mellan PowerShell v4 och v5</span><span class="sxs-lookup"><span data-stu-id="de739-155">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="de739-156">Det finns flera skillnader som du ser när du redigerar konfigurationer i PowerShell 4,0 jämfört med PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="de739-156">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="de739-157">Det här avsnittet visar skillnaderna som du ser relevanta för den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="de739-157">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="de739-158">Flera resurs versioner</span><span class="sxs-lookup"><span data-stu-id="de739-158">Multiple Resource Versions</span></span>

<span data-ttu-id="de739-159">Det finns inte stöd för att installera och använda flera versioner av resurser sida vid sida i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="de739-159">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="de739-160">Om du upptäcker problem med att importera resurser till din konfiguration måste du kontrol lera att du bara har en version av resursen installerad.</span><span class="sxs-lookup"><span data-stu-id="de739-160">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="de739-161">I bilden nedan installeras två versioner av **xPSDesiredStateConfiguration** -modulen.</span><span class="sxs-lookup"><span data-stu-id="de739-161">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Flera resurs versioner som är installerade i mappen](media/import-dscresource/multiple-resource-versions-broken.png)

<span data-ttu-id="de739-163">Kopiera innehållet i den önskade modulens version till den översta nivån i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="de739-163">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Kopiera den önskade versionen till katalogen på den översta nivån](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="de739-165">Resursplats</span><span class="sxs-lookup"><span data-stu-id="de739-165">Resource location</span></span>

<span data-ttu-id="de739-166">När du redigerar och kompilerar konfigurationer kan dina resurser lagras i valfri katalog som anges av din [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="de739-166">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span>
<span data-ttu-id="de739-167">I PowerShell 4,0 kräver LCM att alla DSC-resurspooler lagras under "program Files\WindowsPowerShell\Modules" eller `$pshome\Modules` .</span><span class="sxs-lookup"><span data-stu-id="de739-167">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="de739-168">Från och med PowerShell 5,0 togs detta krav bort och resurspooler kan lagras i valfri katalog som anges av `PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="de739-168">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="de739-169">ModuleVersion tillagt</span><span class="sxs-lookup"><span data-stu-id="de739-169">ModuleVersion added</span></span>

<span data-ttu-id="de739-170">Med början i PowerShell 5,0 `-ModuleVersion` kan du ange vilken version av en modul som ska användas i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="de739-170">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="de739-171">Se även</span><span class="sxs-lookup"><span data-stu-id="de739-171">See also</span></span>

- [<span data-ttu-id="de739-172">Resurser</span><span class="sxs-lookup"><span data-stu-id="de739-172">Resources</span></span>](../resources/resources.md)
