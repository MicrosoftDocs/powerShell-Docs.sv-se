---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med MOF
ms.openlocfilehash: c416fd7cac80d37f1ca1393fa644b4bc15743724
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="4dc80-103">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="4dc80-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="4dc80-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4dc80-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4dc80-105">I det här avsnittet kommer vi definiera schemat för en anpassad resurs i Windows PowerShell önskad tillstånd Configuration (DSC) i en MOF-fil och implementera resursen i en Windows PowerShell-skriptfil.</span><span class="sxs-lookup"><span data-stu-id="4dc80-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="4dc80-106">Den här anpassade resursen är för att skapa och upprätthålla en webbplats.</span><span class="sxs-lookup"><span data-stu-id="4dc80-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="4dc80-107">Skapa MOF-schema</span><span class="sxs-lookup"><span data-stu-id="4dc80-107">Creating the MOF schema</span></span>

<span data-ttu-id="4dc80-108">Schemat definierar egenskaperna för din resurs kan konfigureras med ett DSC-konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="4dc80-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="4dc80-109">Mappstruktur för en MOF-resurs</span><span class="sxs-lookup"><span data-stu-id="4dc80-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="4dc80-110">Skapa följande mappstruktur för att implementera en anpassad DSC-resurs med en MOF-schema.</span><span class="sxs-lookup"><span data-stu-id="4dc80-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="4dc80-111">MOF-schemat har definierats i filen Demo_IISWebsite.schema.mof och resurs-skript har definierats i Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="4dc80-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="4dc80-112">Du kan också kan du skapa en fil för modulen manifestet (psd1).</span><span class="sxs-lookup"><span data-stu-id="4dc80-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="4dc80-113">Observera att det är nödvändigt att skapa en mapp med namnet DSCResources under mappen på översta nivån och att mapp för varje resurs måste ha samma namn som resursen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="4dc80-114">Innehållet i MOF-filen</span><span class="sxs-lookup"><span data-stu-id="4dc80-114">The contents of the MOF file</span></span>

<span data-ttu-id="4dc80-115">Följande är ett exempel MOF-fil som kan användas för en anpassad webbplats-resurs.</span><span class="sxs-lookup"><span data-stu-id="4dc80-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="4dc80-116">Om du vill följa det här exemplet, sparar det här schemat till en fil och anropa filen *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="4dc80-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="4dc80-117">Observera följande om föregående kod:</span><span class="sxs-lookup"><span data-stu-id="4dc80-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="4dc80-118">`FriendlyName`Definierar namnet som du kan använda för att referera till den här anpassade resursen i DSC-konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="4dc80-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="4dc80-119">I det här exemplet `Website` motsvarar det egna namnet `Archive` för den inbyggda Arkiv-resursen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="4dc80-120">Den klass som du definierar för din anpassade resursen måste vara härledd från `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="4dc80-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="4dc80-121">Typ-kvalificeraren `[Key]`på en egenskap som anger att den här egenskapen unikt identifierar resursinstansen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="4dc80-122">Minst en `[Key]` egenskapen måste anges.</span><span class="sxs-lookup"><span data-stu-id="4dc80-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="4dc80-123">Den `[Required]` kvalificerare anger att egenskapen är obligatorisk (ett värde måste anges i alla konfigurationsskript som använder den här resursen).</span><span class="sxs-lookup"><span data-stu-id="4dc80-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="4dc80-124">Den `[write]` kvalificerare anger att den här egenskapen är valfri när du använder den anpassade resursen i ett konfigurationsskript.</span><span class="sxs-lookup"><span data-stu-id="4dc80-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="4dc80-125">Den `[read]` kvalificerare anger att en egenskap inte kan anges med en konfiguration, och enbart för rapportering.</span><span class="sxs-lookup"><span data-stu-id="4dc80-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="4dc80-126">`Values`begränsar vilka värden som kan tilldelas till egenskapen i listan över värden som definieras i `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="4dc80-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="4dc80-127">Mer information finns i [ValueMap och värdet kvalificerare](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="4dc80-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="4dc80-128">Inklusive en egenskap kallas `Ensure` med värden `Present` och `Absent` i din resurs rekommenderas för att bibehålla en konsekvent stil med inbyggda DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="4dc80-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="4dc80-129">Ett filnamn schemat för den anpassade resursen på följande sätt: `classname.schema.mof`, där `classname` identifierare som följer den `class` nyckelord i din schemadefinition.</span><span class="sxs-lookup"><span data-stu-id="4dc80-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="4dc80-130">Resurs-skript</span><span class="sxs-lookup"><span data-stu-id="4dc80-130">Writing the resource script</span></span>

<span data-ttu-id="4dc80-131">Skriptet resurs implementerar logik för resursen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="4dc80-132">Du måste inkludera tre funktioner som anropas i den här modulen **Get-TargetResource**, **Set TargetResource**, och **Test TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="4dc80-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="4dc80-133">Alla tre funktioner måste vidta en parameteruppsättning som är identisk med en uppsättning egenskaper som definierats i MOF-schema som du skapade för din resurs.</span><span class="sxs-lookup"><span data-stu-id="4dc80-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="4dc80-134">I detta dokument kallas den här uppsättningen egenskaper ”resursegenskaper”.</span><span class="sxs-lookup"><span data-stu-id="4dc80-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="4dc80-135">Dessa tre funktioner i en fil kallad <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="4dc80-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="4dc80-136">I följande exempel lagras funktionerna i en fil med namnet Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="4dc80-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="4dc80-137">**Obs**: när du kör samma konfigurationsskript för din resurs mer än en gång, får du några fel och resursen ska befinna sig i samma tillstånd som körs skriptet en gång.</span><span class="sxs-lookup"><span data-stu-id="4dc80-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="4dc80-138">För att åstadkomma detta, se till att din **Get-TargetResource** och **Test TargetResource** funktioner Låt resursen oförändrade och den anropar den **Set-TargetResource**fungerar mer än en gång i en sekvens med samma parameter värden motsvarar alltid anropar den en gång.</span><span class="sxs-lookup"><span data-stu-id="4dc80-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="4dc80-139">I den **Get-TargetResource** fungera implementering, använda viktiga resurser egenskapsvärden som tillhandahålls som parametrar för att kontrollera status för den angivna resurs-instansen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="4dc80-140">Den här funktionen måste returnera en hash-tabell som listar alla resursegenskaper som nycklar och de faktiska värdena för dessa egenskaper som motsvarande värden.</span><span class="sxs-lookup"><span data-stu-id="4dc80-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="4dc80-141">Följande kod visar ett exempel.</span><span class="sxs-lookup"><span data-stu-id="4dc80-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
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

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }
  
        $getTargetResourceResult;
}
```

<span data-ttu-id="4dc80-142">Beroende på de värden som har angetts för resursegenskaper i skript för konfigurering av **Set TargetResource** måste göra något av följande:</span><span class="sxs-lookup"><span data-stu-id="4dc80-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="4dc80-143">Skapa en ny webbplats</span><span class="sxs-lookup"><span data-stu-id="4dc80-143">Create a new website</span></span>
* <span data-ttu-id="4dc80-144">Uppdatera en befintlig webbplats</span><span class="sxs-lookup"><span data-stu-id="4dc80-144">Update an existing website</span></span>
* <span data-ttu-id="4dc80-145">Ta bort en befintlig webbplats</span><span class="sxs-lookup"><span data-stu-id="4dc80-145">Delete an existing website</span></span>

<span data-ttu-id="4dc80-146">Följande exempel illustrerar detta.</span><span class="sxs-lookup"><span data-stu-id="4dc80-146">The following example illustrates this.</span></span>

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
 
    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="4dc80-147">Slutligen den **Test TargetResource** funktionen måste vara samma parameter anges som **Get-TargetResource** och **Set TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="4dc80-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="4dc80-148">I implementeringen av **Test TargetResource**, kontrollera status för resurs-instans som har angetts i parametrarna nyckel.</span><span class="sxs-lookup"><span data-stu-id="4dc80-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="4dc80-149">Om den aktuella statusen för resurs-instans inte matchar de värden som anges i parameteruppsättningen returnera **$false**.</span><span class="sxs-lookup"><span data-stu-id="4dc80-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="4dc80-150">I annat fall returneras **$true**.</span><span class="sxs-lookup"><span data-stu-id="4dc80-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="4dc80-151">I följande kod implementerar den **Test TargetResource** funktion.</span><span class="sxs-lookup"><span data-stu-id="4dc80-151">The following code implements the **Test-TargetResource** function.</span></span>

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

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to 
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="4dc80-152">**Obs**: för enklare felsökning använder den **Write-Verbose** cmdlet i implementeringen av föregående tre funktioner.</span><span class="sxs-lookup"><span data-stu-id="4dc80-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span> 
><span data-ttu-id="4dc80-153">Denna cmdlet skriver texten till den utförliga meddelandeströmmen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-153">This cmdlet writes text to the verbose message stream.</span></span> 
><span data-ttu-id="4dc80-154">Som standard visas inte den utförliga meddelandeströmmen, men du kan visa den genom att ändra värdet för den **$VerbosePreference** variabel eller med hjälp av den **utförlig** parameter i DSC-cmdlets = ny.</span><span class="sxs-lookup"><span data-stu-id="4dc80-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="4dc80-155">Skapa modulmanifestet</span><span class="sxs-lookup"><span data-stu-id="4dc80-155">Creating the module manifest</span></span>

<span data-ttu-id="4dc80-156">Använd slutligen den **ny ModuleManifest** för att definiera en <ResourceName>.psd1 fil för anpassad resurs-modulen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="4dc80-157">När du anropar den här cmdleten, referera till skriptfilen för modulen (.psm1) som beskrivs i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4dc80-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="4dc80-158">Inkludera **Get-TargetResource**, **Set TargetResource**, och **Test TargetResource** i listan över funktioner att exportera.</span><span class="sxs-lookup"><span data-stu-id="4dc80-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="4dc80-159">Följande är ett exempel manifestfilen.</span><span class="sxs-lookup"><span data-stu-id="4dc80-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="4dc80-160">Supporting PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4dc80-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="4dc80-161">**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="4dc80-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4dc80-162">Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](configurations.md) resurs förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="4dc80-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="4dc80-163">Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="4dc80-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="4dc80-164">Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="4dc80-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="4dc80-165">Följande kod skulle till exempel skriva användarkontext som resursen körs under till dataströmmen utförliga utdata:</span><span class="sxs-lookup"><span data-stu-id="4dc80-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```




