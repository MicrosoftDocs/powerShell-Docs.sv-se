---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med MOF
description: Den här artikeln definierar schemat för en anpassad DSC-resurs i en MOF-fil och implementerar resursen i en PowerShell-skriptfil.
ms.openlocfilehash: e79a37699c468b2c55c307c96f1c193a2c1595b3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667189"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="227af-104">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="227af-104">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="227af-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="227af-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="227af-106">I den här artikeln definierar vi schemat för en anpassad DSC-resurs (Desired State Configuration) i Windows PowerShell i en MOF-fil och implementerar resursen i en Windows PowerShell-skriptfil.</span><span class="sxs-lookup"><span data-stu-id="227af-106">In this article, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span>
<span data-ttu-id="227af-107">Den här anpassade resursen används för att skapa och underhålla en webbplats.</span><span class="sxs-lookup"><span data-stu-id="227af-107">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="227af-108">Skapa MOF-schemat</span><span class="sxs-lookup"><span data-stu-id="227af-108">Creating the MOF schema</span></span>

<span data-ttu-id="227af-109">Schemat definierar egenskaperna för din resurs som kan konfigureras med ett DSC-konfigurations skript.</span><span class="sxs-lookup"><span data-stu-id="227af-109">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="227af-110">Mappstruktur för en MOF-resurs</span><span class="sxs-lookup"><span data-stu-id="227af-110">Folder structure for a MOF resource</span></span>

<span data-ttu-id="227af-111">Skapa följande mappstruktur om du vill implementera en anpassad DSC-resurs med ett MOF-schema.</span><span class="sxs-lookup"><span data-stu-id="227af-111">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="227af-112">MOF-schemat definieras i filen `Demo_IISWebsite.schema.mof` och resurs skriptet definieras i `Demo_IISWebsite.psm1` .</span><span class="sxs-lookup"><span data-stu-id="227af-112">The MOF schema is defined in the file `Demo_IISWebsite.schema.mof`, and the resource script is defined in `Demo_IISWebsite.psm1`.</span></span> <span data-ttu-id="227af-113">Du kan också skapa en modul manifest fil (psd1).</span><span class="sxs-lookup"><span data-stu-id="227af-113">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

> [!NOTE]
> <span data-ttu-id="227af-114">Det är nödvändigt att skapa en mapp med namnet DSCResources under mappen på den översta nivån och att mappen för varje resurs måste ha samma namn som resursen.</span><span class="sxs-lookup"><span data-stu-id="227af-114">It is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="227af-115">MOF-filens innehåll</span><span class="sxs-lookup"><span data-stu-id="227af-115">The contents of the MOF file</span></span>

<span data-ttu-id="227af-116">Följande är ett exempel på en MOF-fil som kan användas för en anpassad webbplats resurs.</span><span class="sxs-lookup"><span data-stu-id="227af-116">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="227af-117">Om du vill följa det här exemplet sparar du schemat till en fil och anropar filen `Demo_IISWebsite.schema.mof` .</span><span class="sxs-lookup"><span data-stu-id="227af-117">To follow this example, save this schema to a file, and call the file `Demo_IISWebsite.schema.mof`.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="227af-118">Observera följande om föregående kod:</span><span class="sxs-lookup"><span data-stu-id="227af-118">Note the following about the previous code:</span></span>

- <span data-ttu-id="227af-119">`FriendlyName` definierar det namn som du kan använda för att referera till den här anpassade resursen i DSC-konfigurations skript.</span><span class="sxs-lookup"><span data-stu-id="227af-119">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="227af-120">I det här exemplet `Website` motsvarar det egna namnet `Archive` för den inbyggda Arkiv resursen.</span><span class="sxs-lookup"><span data-stu-id="227af-120">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
- <span data-ttu-id="227af-121">Den klass som du definierar för din anpassade resurs måste vara härledd från `OMI_BaseResource` .</span><span class="sxs-lookup"><span data-stu-id="227af-121">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
- <span data-ttu-id="227af-122">Typen Qualifier, `[Key]` i en egenskap anger att den här egenskapen unikt identifierar resurs instansen.</span><span class="sxs-lookup"><span data-stu-id="227af-122">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="227af-123">Minst en `[Key]` egenskap krävs.</span><span class="sxs-lookup"><span data-stu-id="227af-123">At least one `[Key]` property is required.</span></span>
- <span data-ttu-id="227af-124">`[Required]`Kvalificeraren anger att egenskapen är obligatorisk (ett värde måste anges i alla konfigurations skript som använder den här resursen).</span><span class="sxs-lookup"><span data-stu-id="227af-124">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
- <span data-ttu-id="227af-125">`[write]`Kvalificeraren anger att den här egenskapen är valfri när du använder den anpassade resursen i ett konfigurations skript.</span><span class="sxs-lookup"><span data-stu-id="227af-125">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="227af-126">`[read]`Kvalificeraren anger att en egenskap inte kan ställas in av en konfiguration och endast är avsedd för rapportering.</span><span class="sxs-lookup"><span data-stu-id="227af-126">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
- <span data-ttu-id="227af-127">`Values` begränsar de värden som kan tilldelas till egenskapen till listan över värden som definierats i `ValueMap` .</span><span class="sxs-lookup"><span data-stu-id="227af-127">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="227af-128">Mer information finns i [ValueMap och värde kvalificerare](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="227af-128">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
- <span data-ttu-id="227af-129">Att inkludera en egenskap som kallas `Ensure` med värden `Present` och `Absent` i din resurs rekommenderas som ett sätt att underhålla ett konsekvent format med inbyggda DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="227af-129">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
- <span data-ttu-id="227af-130">Namnge schema filen för din anpassade resurs enligt följande: `classname.schema.mof` , där `classname` är identifieraren som följer `class` nyckelordet i schema definitionen.</span><span class="sxs-lookup"><span data-stu-id="227af-130">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="227af-131">Skriver resurs skriptet</span><span class="sxs-lookup"><span data-stu-id="227af-131">Writing the resource script</span></span>

<span data-ttu-id="227af-132">Resurs skriptet implementerar logiken för resursen.</span><span class="sxs-lookup"><span data-stu-id="227af-132">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="227af-133">I den här modulen måste du inkludera tre funktioner som kallas `Get-TargetResource` , `Set-TargetResource` , och `Test-TargetResource` .</span><span class="sxs-lookup"><span data-stu-id="227af-133">In this module, you must include three functions called `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource`.</span></span> <span data-ttu-id="227af-134">Alla tre funktioner måste ha en parameter uppsättning som är identisk med uppsättningen med egenskaper som definierats i MOF-schemat som du skapade för din resurs.</span><span class="sxs-lookup"><span data-stu-id="227af-134">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="227af-135">I det här dokumentet kallas den här uppsättningen egenskaper för "resurs egenskaper".</span><span class="sxs-lookup"><span data-stu-id="227af-135">In this document, this set of properties is referred to as the "resource properties."</span></span> <span data-ttu-id="227af-136">Lagra dessa tre funktioner i en fil med namnet `<ResourceName>.psm1` .</span><span class="sxs-lookup"><span data-stu-id="227af-136">Store these three functions in a file called `<ResourceName>.psm1`.</span></span> <span data-ttu-id="227af-137">I följande exempel lagras funktionerna i en fil med namnet `Demo_IISWebsite.psm1` .</span><span class="sxs-lookup"><span data-stu-id="227af-137">In the following example, the functions are stored in a file called `Demo_IISWebsite.psm1`.</span></span>

> [!NOTE]
> <span data-ttu-id="227af-138">När du kör samma konfigurations skript på din resurs mer än en gång, bör du få inga fel och resursen ska finnas kvar i samma tillstånd som att köra skriptet en gång.</span><span class="sxs-lookup"><span data-stu-id="227af-138">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="227af-139">För att åstadkomma detta måste du se till att dina `Get-TargetResource` och- `Test-TargetResource` funktionerna lämnar resursen oförändrade och att anropet till `Set-TargetResource` funktionen mer än en gång i en sekvens med samma parameter värden alltid motsvarar att anropa den en gång.</span><span class="sxs-lookup"><span data-stu-id="227af-139">To accomplish this, ensure that your `Get-TargetResource` and `Test-TargetResource` functions leave the resource unchanged, and that invoking the `Set-TargetResource` function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="227af-140">I `Get-TargetResource` funktions implementeringen använder du de nyckel resurs egenskaps värden som anges som parametrar för att kontrol lera status för den angivna resurs instansen.</span><span class="sxs-lookup"><span data-stu-id="227af-140">In the `Get-TargetResource` function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="227af-141">Den här funktionen måste returnera en hash-tabell som visar alla resurs egenskaper som nycklar och de faktiska värdena för dessa egenskaper som motsvarande värden.</span><span class="sxs-lookup"><span data-stu-id="227af-141">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="227af-142">Följande kod visar ett exempel.</span><span class="sxs-lookup"><span data-stu-id="227af-142">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance
# specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <#
          Insert logic that uses the mandatory parameter values to get the website and
          assign it to a variable called $Website
          Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise
        #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
            Name = $Website.Name
            Ensure = $ensureResult
            PhysicalPath = $Website.physicalPath
            State = $Website.state
            ID = $Website.id
            ApplicationPool = $Website.applicationPool
            Protocol = $Website.bindings.Collection.protocol
            Binding = $Website.bindings.Collection.bindingInformation
        }

        $getTargetResourceResult
}
```

<span data-ttu-id="227af-143">Beroende på vilka värden som anges för resurs egenskaperna i konfigurations skriptet `Set-TargetResource` måste du göra något av följande:</span><span class="sxs-lookup"><span data-stu-id="227af-143">Depending on the values that are specified for the resource properties in the configuration script, the `Set-TargetResource` must do one of the following:</span></span>

- <span data-ttu-id="227af-144">Skapa en ny webbplats</span><span class="sxs-lookup"><span data-stu-id="227af-144">Create a new website</span></span>
- <span data-ttu-id="227af-145">Uppdatera en befintlig webbplats</span><span class="sxs-lookup"><span data-stu-id="227af-145">Update an existing website</span></span>
- <span data-ttu-id="227af-146">Ta bort en befintlig webbplats</span><span class="sxs-lookup"><span data-stu-id="227af-146">Delete an existing website</span></span>

<span data-ttu-id="227af-147">I följande exempel visas detta.</span><span class="sxs-lookup"><span data-stu-id="227af-147">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <#
        If Ensure is set to "Present" and the website specified in the mandatory input parameters
          does not exist, then create it using the specified parameter values
        Else, if Ensure is set to "Present" and the website does exist, then update its properties
          to match the values provided in the non-mandatory parameter values
        Else, if Ensure is set to "Absent" and the website does not exist, then do nothing
        Else, if Ensure is set to "Absent" and the website does exist, then delete the website
    #>
}
```

<span data-ttu-id="227af-148">Slutligen `Test-TargetResource` måste funktionen ta samma parameter uppsättning som `Get-TargetResource` och `Set-TargetResource` .</span><span class="sxs-lookup"><span data-stu-id="227af-148">Finally, the `Test-TargetResource` function must take the same parameter set as `Get-TargetResource` and `Set-TargetResource`.</span></span> <span data-ttu-id="227af-149">I implementeringen av `Test-TargetResource` kontrollerar du statusen för den resurs instans som anges i nyckel parametrarna.</span><span class="sxs-lookup"><span data-stu-id="227af-149">In your implementation of `Test-TargetResource`, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="227af-150">Om resurs instansens faktiska status inte matchar värdena som anges i parameter uppsättningen returnerar `$false` .</span><span class="sxs-lookup"><span data-stu-id="227af-150">If the actual status of the resource instance does not match the values specified in the parameter set, return `$false`.</span></span> <span data-ttu-id="227af-151">Annars kan du gå tillbaka `$true` .</span><span class="sxs-lookup"><span data-stu-id="227af-151">Otherwise, return `$true`.</span></span>

<span data-ttu-id="227af-152">I följande kod implementeras `Test-TargetResource` funktionen.</span><span class="sxs-lookup"><span data-stu-id="227af-152">The following code implements the `Test-TargetResource` function.</span></span>

```powershell
function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([System.Boolean])]
    param
    (
        [ValidateSet("Present","Absent")]
        [System.String]
        $Ensure,

        [parameter(Mandatory = $true)]
        [System.String]
        $Name,

        [parameter(Mandatory = $true)]
        [System.String]
        $PhysicalPath,

        [ValidateSet("Started","Stopped")]
        [System.String]
        $State,

        [System.String[]]
        $Protocol,

        [System.String[]]
        $BindingData,

        [System.String]
        $ApplicationPool
    )

    # Get the current state
    $currentState = Get-TargetResource -Ensure $Ensure -Name $Name -PhysicalPath $PhysicalPath -State $State -ApplicationPool $ApplicationPool -BindingInfo $BindingInfo -Protocol $Protocol

    # Write-Verbose "Use this cmdlet to deliver information about command processing."

    # Write-Debug "Use this cmdlet to write debug information while troubleshooting."

    # Include logic to
    $result = [System.Boolean]
    # Add logic to test whether the website is present and its status matches the supplied
    # parameter values. If it does, return true. If it does not, return false.
    $result
}
```

> [!NOTE]
> <span data-ttu-id="227af-153">För enklare fel sökning använder du `Write-Verbose` cmdleten i din implementering av de föregående tre funktionerna.</span><span class="sxs-lookup"><span data-stu-id="227af-153">For easier debugging, use the `Write-Verbose` cmdlet in your implementation of the previous three functions.</span></span> <span data-ttu-id="227af-154">Denna cmdlet skriver text till data strömmen för utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="227af-154">This cmdlet writes text to the verbose message stream.</span></span> <span data-ttu-id="227af-155">Den utförliga meddelande strömmen visas som standard inte, men du kan visa den genom att ändra värdet för variabeln **$VerbosePreference** eller genom att använda **verbose** -parametern i DSC-cmdletar = ny.</span><span class="sxs-lookup"><span data-stu-id="227af-155">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="227af-156">Skapar modulens manifest</span><span class="sxs-lookup"><span data-stu-id="227af-156">Creating the module manifest</span></span>

<span data-ttu-id="227af-157">Använd slutligen `New-ModuleManifest` cmdleten för att definiera en `<ResourceName>.psd1` fil för modulen för anpassad resurs.</span><span class="sxs-lookup"><span data-stu-id="227af-157">Finally, use the `New-ModuleManifest` cmdlet to define a `<ResourceName>.psd1` file for your custom resource module.</span></span> <span data-ttu-id="227af-158">När du anropar denna cmdlet refererar du till script module-filen (. psm1) som beskrivs i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="227af-158">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="227af-159">Inkludera `Get-TargetResource` , `Set-TargetResource` och `Test-TargetResource` i listan över funktioner som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="227af-159">Include `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` in the list of functions to export.</span></span> <span data-ttu-id="227af-160">Följande är ett exempel på en manifest fil.</span><span class="sxs-lookup"><span data-stu-id="227af-160">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="227af-161">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="227af-161">Supporting PsDscRunAsCredential</span></span>

> [!Note]
> <span data-ttu-id="227af-162">**PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="227af-162">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="227af-163">Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="227af-163">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="227af-164">Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="227af-164">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="227af-165">Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den automatiska variabeln `$PsDscContext` .</span><span class="sxs-lookup"><span data-stu-id="227af-165">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="227af-166">Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:</span><span class="sxs-lookup"><span data-stu-id="227af-166">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="227af-167">Starta om noden</span><span class="sxs-lookup"><span data-stu-id="227af-167">Rebooting the Node</span></span>

<span data-ttu-id="227af-168">Om de åtgärder som vidtas i `Set-TargetResource` funktionen kräver omstart kan du använda en global flagga för att INSTRUERA LCM att starta om noden.</span><span class="sxs-lookup"><span data-stu-id="227af-168">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="227af-169">Den här omstarten sker direkt efter att `Set-TargetResource` funktionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="227af-169">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="227af-170">I din `Set-TargetResource` funktion lägger du till följande kodrad.</span><span class="sxs-lookup"><span data-stu-id="227af-170">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="227af-171">För att LCM ska kunna starta om noden måste flaggan **RebootNodeIfNeeded** anges till `$true` .</span><span class="sxs-lookup"><span data-stu-id="227af-171">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span>
<span data-ttu-id="227af-172">Inställningen **ActionAfterReboot** bör också ställas in på **ContinueConfiguration** , vilket är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="227af-172">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration** , which is the default.</span></span> <span data-ttu-id="227af-173">Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)eller [konfigurera den lokala Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="227af-173">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
