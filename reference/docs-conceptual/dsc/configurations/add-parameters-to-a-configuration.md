---
ms.date: 12/12/2018
keywords: DSC, PowerShell, resurs, Galleri, installation
title: Lägga till parametrar i en konfiguration
description: DSC-konfigurationer kan vara parameterstyrda för att tillåta fler dynamiska konfigurationer utifrån användarindata.
ms.openlocfilehash: aea230d34994a7b20076559c44990abe554d5395
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656814"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="6ada8-104">Lägga till parametrar i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="6ada8-104">Add Parameters to a Configuration</span></span>

<span data-ttu-id="6ada8-105">Precis som-funktioner kan [konfigurationer](configurations.md) vara parameterstyrda för att tillåta fler dynamiska konfigurationer utifrån användarindata.</span><span class="sxs-lookup"><span data-stu-id="6ada8-105">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="6ada8-106">Stegen liknar de som beskrivs i [Functions med parametrar](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="6ada8-106">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="6ada8-107">Det här exemplet börjar med en grundläggande konfiguration som konfigurerar "Spooler"-tjänsten att köras.</span><span class="sxs-lookup"><span data-stu-id="6ada8-107">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="6ada8-108">Inbyggda konfigurations parametrar</span><span class="sxs-lookup"><span data-stu-id="6ada8-108">Built-in Configuration parameters</span></span>

<span data-ttu-id="6ada8-109">Till skillnad från en Function-CmdletBinding, lägger attributet [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) till inga funktioner.</span><span class="sxs-lookup"><span data-stu-id="6ada8-109">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="6ada8-110">Förutom [vanliga parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters)kan konfigurationer också använda följande inbyggda parametrar, utan att du behöver definiera dem.</span><span class="sxs-lookup"><span data-stu-id="6ada8-110">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|        <span data-ttu-id="6ada8-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="6ada8-111">Parameter</span></span>        |                                         <span data-ttu-id="6ada8-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6ada8-112">Description</span></span>                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | <span data-ttu-id="6ada8-113">Används i definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6ada8-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-DependsOn`            | <span data-ttu-id="6ada8-114">Används i definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6ada8-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-PSDSCRunAsCredential` | <span data-ttu-id="6ada8-115">Används i definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6ada8-115">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-ConfigurationData`    | <span data-ttu-id="6ada8-116">Används för att skicka strukturerade [konfigurations data](configData.md) för användning i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6ada8-116">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span> |
| `-OutputPath`           | <span data-ttu-id="6ada8-117">Används för att ange var din " \<computername\> . MOF"-fil ska kompileras</span><span class="sxs-lookup"><span data-stu-id="6ada8-117">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>                      |

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="6ada8-118">Lägga till egna parametrar i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6ada8-118">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="6ada8-119">Förutom de inbyggda parametrarna kan du också lägga till egna parametrar i dina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="6ada8-119">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span>
<span data-ttu-id="6ada8-120">Parameter blocket hamnar direkt inuti konfigurations deklarationen, precis som en funktion.</span><span class="sxs-lookup"><span data-stu-id="6ada8-120">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="6ada8-121">Ett konfigurations parameter block ska vara utanför alla **Node** -deklarationer och över alla *import* -instruktioner.</span><span class="sxs-lookup"><span data-stu-id="6ada8-121">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="6ada8-122">Genom att lägga till parametrar kan du göra dina konfigurationer mer robusta och dynamiska.</span><span class="sxs-lookup"><span data-stu-id="6ada8-122">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="6ada8-123">Lägg till en ComputerName-parameter</span><span class="sxs-lookup"><span data-stu-id="6ada8-123">Add a ComputerName parameter</span></span>

<span data-ttu-id="6ada8-124">Den första parametern som du kan lägga till är en `-Computername` parameter så att du dynamiskt kan kompilera en ". MOF"-fil för alla `-Computername` som du skickar till din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6ada8-124">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="6ada8-125">Precis som funktioner kan du också definiera ett standardvärde, om användaren inte skickar något värde för `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="6ada8-125">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="6ada8-126">I konfigurationen kan du ange din `-ComputerName` parameter när du definierar ett Node-block.</span><span class="sxs-lookup"><span data-stu-id="6ada8-126">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="6ada8-127">Anropa konfigurationen med parametrar</span><span class="sxs-lookup"><span data-stu-id="6ada8-127">Calling your Configuration with parameters</span></span>

<span data-ttu-id="6ada8-128">När du har lagt till parametrar i konfigurationen kan du använda dem precis som med en-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ada8-128">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="6ada8-129">Kompilera flera MOF-filer</span><span class="sxs-lookup"><span data-stu-id="6ada8-129">Compiling multiple .mof files</span></span>

<span data-ttu-id="6ada8-130">Node-blocket kan också acceptera en kommaavgränsad lista med dator namn och genererar "MOF"-filer för var och en.</span><span class="sxs-lookup"><span data-stu-id="6ada8-130">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="6ada8-131">Du kan köra följande exempel för att generera ". MOF"-filer för alla datorer som skickas till `-ComputerName` parametern.</span><span class="sxs-lookup"><span data-stu-id="6ada8-131">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String[]]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="6ada8-132">Avancerade parametrar i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6ada8-132">Advanced parameters in Configurations</span></span>

<span data-ttu-id="6ada8-133">Förutom en `-ComputerName` parameter kan vi lägga till parametrar för tjänstens namn och tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6ada8-133">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span>
<span data-ttu-id="6ada8-134">I följande exempel lägger du till ett parameter block med en `-ServiceName` parameter och använder den för att dynamiskt definiera **tjänst** resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="6ada8-134">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="6ada8-135">Den lägger också till en `-State` parameter för att dynamiskt definiera **statusen** i **tjänst** resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="6ada8-135">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="6ada8-136">I mer avancerade scenarier kan det vara mer meningsfullt att flytta dina dynamiska data till en strukturerad [konfigurations data](configData.md).</span><span class="sxs-lookup"><span data-stu-id="6ada8-136">In more advanced scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="6ada8-137">Exempel konfigurationen tar nu en dynamisk `$ServiceName` , men om ingen anges kompileras resultatet i ett fel.</span><span class="sxs-lookup"><span data-stu-id="6ada8-137">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="6ada8-138">Du kan lägga till ett standardvärde som det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="6ada8-138">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="6ada8-139">I den här instansen är det mer meningsfullt att bara tvinga användaren att ange ett värde för `$ServiceName` parametern.</span><span class="sxs-lookup"><span data-stu-id="6ada8-139">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="6ada8-140">Med `parameter` attributet kan du lägga till ytterligare verifiering och stöd för pipelinering i konfigurationens parametrar.</span><span class="sxs-lookup"><span data-stu-id="6ada8-140">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="6ada8-141">Lägg till `parameter` Attribute-blocket som i exemplet nedan, ovanför parameter deklarationen.</span><span class="sxs-lookup"><span data-stu-id="6ada8-141">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="6ada8-142">Du kan ange argument för varje `parameter` attribut, för att styra aspekter av den definierade parametern.</span><span class="sxs-lookup"><span data-stu-id="6ada8-142">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="6ada8-143">I följande exempel görs `$ServiceName` en **obligatorisk** parameter.</span><span class="sxs-lookup"><span data-stu-id="6ada8-143">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="6ada8-144">För `$State` -parametern skulle vi vilja hindra användaren från att ange värden utanför en fördefinierad uppsättning (som att köra, stoppa) `ValidationSet*` attributet skulle hindra användaren från att ange värden utanför en fördefinierad uppsättning (t. ex. igång, stoppad).</span><span class="sxs-lookup"><span data-stu-id="6ada8-144">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="6ada8-145">I följande exempel läggs `ValidationSet` attributet till i `$State` parametern.</span><span class="sxs-lookup"><span data-stu-id="6ada8-145">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="6ada8-146">Eftersom vi inte vill göra `$State` parametern **obligatorisk** , måste du lägga till ett standardvärde för den.</span><span class="sxs-lookup"><span data-stu-id="6ada8-146">Since we do not want to make the `$State` parameter **Mandatory** , we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="6ada8-147">Du behöver inte ange ett `parameter` attribut när du använder ett- `validation` attribut.</span><span class="sxs-lookup"><span data-stu-id="6ada8-147">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="6ada8-148">Du kan läsa mer om `parameter` verifierings-och verifierings-attributen i [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="6ada8-148">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="6ada8-149">Helt parametriserad konfiguration</span><span class="sxs-lookup"><span data-stu-id="6ada8-149">Fully parameterized Configuration</span></span>

<span data-ttu-id="6ada8-150">Nu har vi en parametriserad konfiguration som tvingar användaren att ange en `-InstanceName` , `-ServiceName` och verifierar `-State` parametern.</span><span class="sxs-lookup"><span data-stu-id="6ada8-150">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="6ada8-151">Se även</span><span class="sxs-lookup"><span data-stu-id="6ada8-151">See also</span></span>

- [<span data-ttu-id="6ada8-152">Skrivhjälp för DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6ada8-152">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="6ada8-153">Dynamiska konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6ada8-153">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="6ada8-154">Använd konfigurations data i dina konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6ada8-154">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="6ada8-155">Separata konfigurations-och miljö data</span><span class="sxs-lookup"><span data-stu-id="6ada8-155">Separate configuration and environment data</span></span>](separatingEnvData.md)
