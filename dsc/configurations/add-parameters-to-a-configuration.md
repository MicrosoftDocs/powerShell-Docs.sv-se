---
ms.date: 12/12/2018
keywords: DSC, PowerShell, resurs, Galleri, installation
title: Lägga till parametrar i en konfiguration
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386318"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="fcd88-103">Lägga till parametrar i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="fcd88-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="fcd88-104">Precis som-funktioner kan [konfigurationer](configurations.md) vara parameterstyrda för att tillåta fler dynamiska konfigurationer utifrån användarindata.</span><span class="sxs-lookup"><span data-stu-id="fcd88-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="fcd88-105">Stegen liknar de som beskrivs i [Functions med parametrar](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="fcd88-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="fcd88-106">Det här exemplet börjar med en grundläggande konfiguration som konfigurerar "Spooler"-tjänsten att köras.</span><span class="sxs-lookup"><span data-stu-id="fcd88-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="fcd88-107">Inbyggda konfigurations parametrar</span><span class="sxs-lookup"><span data-stu-id="fcd88-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="fcd88-108">Till skillnad från en Function-CmdletBinding, lägger attributet [](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) till inga funktioner.</span><span class="sxs-lookup"><span data-stu-id="fcd88-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="fcd88-109">Förutom [vanliga parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters)kan konfigurationer också använda följande inbyggda parametrar, utan att du behöver definiera dem.</span><span class="sxs-lookup"><span data-stu-id="fcd88-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="fcd88-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="fcd88-110">Parameter</span></span>  |<span data-ttu-id="fcd88-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fcd88-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="fcd88-112">Används i definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="fcd88-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="fcd88-113">Används i definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="fcd88-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="fcd88-114">Används i definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="fcd88-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="fcd88-115">Används för att skicka strukturerade [konfigurations data](configData.md) för användning i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fcd88-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="fcd88-116">Används för att ange var din\<"\>ComputerName. MOF"-fil ska kompileras</span><span class="sxs-lookup"><span data-stu-id="fcd88-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="fcd88-117">Lägga till egna parametrar i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="fcd88-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="fcd88-118">Förutom de inbyggda parametrarna kan du också lägga till egna parametrar i dina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="fcd88-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="fcd88-119">Parameter blocket hamnar direkt inuti konfigurations deklarationen, precis som en funktion.</span><span class="sxs-lookup"><span data-stu-id="fcd88-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="fcd88-120">Ett konfigurations parameter block ska vara utanför alla **Node** -deklarationer och över alla *import* -instruktioner.</span><span class="sxs-lookup"><span data-stu-id="fcd88-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="fcd88-121">Genom att lägga till parametrar kan du göra dina konfigurationer mer robusta och dynamiska.</span><span class="sxs-lookup"><span data-stu-id="fcd88-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="fcd88-122">Lägg till en ComputerName-parameter</span><span class="sxs-lookup"><span data-stu-id="fcd88-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="fcd88-123">Den första parametern som du kan lägga till `-Computername` är en parameter så att du dynamiskt kan kompilera en ". MOF" `-Computername` -fil för alla som du skickar till din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fcd88-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="fcd88-124">Precis som funktioner kan du också definiera ett standardvärde, om användaren inte skickar något värde för`-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="fcd88-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="fcd88-125">I konfigurationen kan du ange din `-ComputerName` parameter när du definierar ett Node-block.</span><span class="sxs-lookup"><span data-stu-id="fcd88-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="fcd88-126">Anropa konfigurationen med parametrar</span><span class="sxs-lookup"><span data-stu-id="fcd88-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="fcd88-127">När du har lagt till parametrar i konfigurationen kan du använda dem precis som med en-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcd88-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="fcd88-128">Kompilera flera MOF-filer</span><span class="sxs-lookup"><span data-stu-id="fcd88-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="fcd88-129">Node-blocket kan också acceptera en kommaavgränsad lista med dator namn och genererar "MOF"-filer för var och en.</span><span class="sxs-lookup"><span data-stu-id="fcd88-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="fcd88-130">Du kan köra följande exempel för att generera ". MOF"-filer för alla datorer som skickas till `-ComputerName` parametern.</span><span class="sxs-lookup"><span data-stu-id="fcd88-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="fcd88-131">Avancerade parametrar i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="fcd88-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="fcd88-132">Förutom en `-ComputerName` parameter kan vi lägga till parametrar för tjänstens namn och tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fcd88-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="fcd88-133">I följande exempel lägger du till ett parameter block `-ServiceName` med en parameter och använder den för att dynamiskt definiera **tjänst** resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="fcd88-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="fcd88-134">Den lägger också till `-State` en parameter för att dynamiskt definiera **statusen** i **tjänst** resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="fcd88-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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
> <span data-ttu-id="fcd88-135">I fler advacned-scenarier kan det vara mer meningsfullt att flytta dina dynamiska data till en strukturerad [konfigurations data](configData.md).</span><span class="sxs-lookup"><span data-stu-id="fcd88-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="fcd88-136">Exempel konfigurationen tar nu en dynamisk `$ServiceName`, men om ingen anges kompileras resultatet i ett fel.</span><span class="sxs-lookup"><span data-stu-id="fcd88-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="fcd88-137">Du kan lägga till ett standardvärde som det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="fcd88-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="fcd88-138">I den här instansen är det mer meningsfullt att bara tvinga användaren att ange ett värde för `$ServiceName` parametern.</span><span class="sxs-lookup"><span data-stu-id="fcd88-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="fcd88-139">Med `parameter` attributet kan du lägga till ytterligare verifiering och stöd för pipelinering i konfigurationens parametrar.</span><span class="sxs-lookup"><span data-stu-id="fcd88-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="fcd88-140">Lägg till `parameter` Attribute-blocket som i exemplet nedan, ovanför parameter deklarationen.</span><span class="sxs-lookup"><span data-stu-id="fcd88-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="fcd88-141">Du kan ange argument för varje `parameter` attribut, för att styra aspekter av den definierade parametern.</span><span class="sxs-lookup"><span data-stu-id="fcd88-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="fcd88-142">I följande exempel görs `$ServiceName` en **obligatorisk** parameter.</span><span class="sxs-lookup"><span data-stu-id="fcd88-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="fcd88-143">För- `ValidationSet*`parametern skulle vi vilja hindra användaren från att ange värden utanför en fördefinierad uppsättning (som att köra, stoppa) attributet skulle hindra användaren från att ange värden utanför en fördefinierad uppsättning (som kör, `$State` Stoppad).</span><span class="sxs-lookup"><span data-stu-id="fcd88-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="fcd88-144">I följande exempel läggs `ValidationSet` attributet `$State` till i parametern.</span><span class="sxs-lookup"><span data-stu-id="fcd88-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="fcd88-145">Eftersom vi inte vill göra `$State` parametern **obligatorisk**, måste du lägga till ett standardvärde för den.</span><span class="sxs-lookup"><span data-stu-id="fcd88-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="fcd88-146">Du behöver inte ange ett `parameter` attribut när du använder ett `validation` -attribut.</span><span class="sxs-lookup"><span data-stu-id="fcd88-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="fcd88-147">Du kan läsa mer om `parameter` verifierings-och verifierings-attributen i [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="fcd88-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="fcd88-148">Helt parametriserad konfiguration</span><span class="sxs-lookup"><span data-stu-id="fcd88-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="fcd88-149">Nu har vi en parametriserad konfiguration som tvingar användaren att ange en `-InstanceName`, `-ServiceName`och verifierar `-State` parametern.</span><span class="sxs-lookup"><span data-stu-id="fcd88-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="fcd88-150">Se även</span><span class="sxs-lookup"><span data-stu-id="fcd88-150">See also</span></span>

- [<span data-ttu-id="fcd88-151">Skriv hjälp för DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="fcd88-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="fcd88-152">Dynamiska konfigurationer</span><span class="sxs-lookup"><span data-stu-id="fcd88-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="fcd88-153">Använd konfigurations data i dina konfigurationer</span><span class="sxs-lookup"><span data-stu-id="fcd88-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="fcd88-154">Separata konfigurations-och miljö data</span><span class="sxs-lookup"><span data-stu-id="fcd88-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
