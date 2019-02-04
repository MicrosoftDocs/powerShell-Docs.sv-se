---
ms.date: 12/12/2018
keywords: DSC, powershell, resurs, galleriet, inställning
title: Lägga till parametrar i en konfiguration
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685405"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="4f4a6-103">Lägga till parametrar i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="4f4a6-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="4f4a6-104">Ha funktioner, [konfigurationer](configurations.md) kan parameteriseras för att tillåta mer dynamiska konfigurationer baserat på indata från användaren.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="4f4a6-105">Stegen är samma som beskrivs i [funktioner med parametrar](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="4f4a6-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="4f4a6-106">Det här exemplet börjar med en grundläggande konfiguration som konfigurerar ”Utskriftshanteraren” till ”körs”.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="4f4a6-107">Inbyggda konfigurationsparametrar</span><span class="sxs-lookup"><span data-stu-id="4f4a6-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="4f4a6-108">Till skillnad från en funktion dock den [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attributet lägger till inga funktioner.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="4f4a6-109">Förutom [gemensamma parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters), konfigurationer kan också använda följande inbyggda parametrar, utan att du behöver definiera dem.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="4f4a6-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="4f4a6-110">Parameter</span></span>  |<span data-ttu-id="4f4a6-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4f4a6-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="4f4a6-112">Används för att definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="4f4a6-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="4f4a6-113">Används för att definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="4f4a6-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="4f4a6-114">Används för att definiera [sammansatta konfigurationer](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="4f4a6-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="4f4a6-115">Används för att skicka i strukturerade [konfigurationsdata](configData.md) för användning i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="4f4a6-116">Används för att ange var din ”\<computername\>.mof” filen kompileras</span><span class="sxs-lookup"><span data-stu-id="4f4a6-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="4f4a6-117">Att lägga till dina egna parametrar konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4f4a6-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="4f4a6-118">Förutom de inbyggda parametrarna, kan du också lägga till dina egna parametrar dina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="4f4a6-119">Parameterblocket går direkt i deklarationen konfiguration, precis som en funktion.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="4f4a6-120">En konfiguration Parameterblocket bör finnas utanför någon **nod** deklarationer, och senare någon *importera* instruktioner.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="4f4a6-121">Genom att lägga till parametrar, kan du göra dina konfigurationer mer stabilt och dynamisk.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="4f4a6-122">Lägg till en ComputerName-parameter</span><span class="sxs-lookup"><span data-stu-id="4f4a6-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="4f4a6-123">Den första parametern som du kan lägga till är en `-Computername` parametern så att du kan dynamiskt sammanställa en ”.mof”-fil för alla `-Computername` du skickar till din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="4f4a6-124">Som Functions, kan du också definiera ett standardvärde om användaren inte skickar ett värde för `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="4f4a6-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="4f4a6-125">I din konfiguration kan du sedan ange din `-ComputerName` parameter när du definierar din nod-block.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="4f4a6-126">Anropar din konfiguration med parametrar</span><span class="sxs-lookup"><span data-stu-id="4f4a6-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="4f4a6-127">När du har lagt till parametrar i din konfiguration, kan du använda dem precis som med en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="4f4a6-128">Kompilera flera MOF-filer</span><span class="sxs-lookup"><span data-stu-id="4f4a6-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="4f4a6-129">Noden blocket kan också acceptera en kommaavgränsad lista med datornamn och genererar MOF-filerna för var och en.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="4f4a6-130">Du kan köra i följande exempel för att generera MOF-filerna för alla datorer som skickas till den `-ComputerName` parametern.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="4f4a6-131">Avancerade parametrar i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4f4a6-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="4f4a6-132">Förutom en `-ComputerName` parameter, kan vi lägga till parametrar för tjänstens namn och status.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="4f4a6-133">I följande exempel läggs en Parameterblocket med en `-ServiceName` parametern och används för att definiera dynamiskt den **Service** resource block.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="4f4a6-134">Läggs även en `-State` parametern för att definiera dynamiskt den **tillstånd** i den **Service** resource block.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="4f4a6-135">I fler advacned scenarier kan det vara bättre att flytta dynamiska data till en strukturerade [konfigurationsdata](configData.md).</span><span class="sxs-lookup"><span data-stu-id="4f4a6-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="4f4a6-136">Exempel konfiguration nu tar en dynamisk `$ServiceName`, men om inget annat anges, kompilera uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="4f4a6-137">Du kan lägga till ett standardvärde som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="4f4a6-138">I den här instansen dock är det mer praktiskt att bara tvinga användaren att ange ett värde för den `$ServiceName` parametern.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="4f4a6-139">Den `parameter` attribut kan du lägga till ytterligare verifiering och pipeline stöd till parametrar för din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="4f4a6-140">Ovanför alla parameterdeklaration lägger du till den `parameter` attributet block som i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="4f4a6-141">Du kan ange argument för varje `parameter` attribut för att kontrollen aspekter av definierad parameter.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="4f4a6-142">I följande exempel gör den `$ServiceName` en **obligatorisk** parametern.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="4f4a6-143">För den `$State` parametern, som vi vill hindra användaren från att ange värden utanför en fördefinierad uppsättning (som körs, stoppad) den `ValidationSet*`attributet skulle hindra användaren från att ange värden utanför en fördefinierad uppsättning (till exempel drift, Stoppats).</span><span class="sxs-lookup"><span data-stu-id="4f4a6-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="4f4a6-144">I följande exempel läggs den `ValidationSet` attributet den `$State` parametern.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="4f4a6-145">Eftersom vi inte vill göra den `$State` parametern **obligatorisk**, vi måste lägga till ett standardvärde för den.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="4f4a6-146">Du behöver inte ange en `parameter` attribut när du använder en `validation` attribut.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="4f4a6-147">Du kan läsa mer om den `parameter` och verifiering attribut i [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4f4a6-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="4f4a6-148">Fullständigt parametriserade konfiguration</span><span class="sxs-lookup"><span data-stu-id="4f4a6-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="4f4a6-149">Nu har vi en parametriserade konfiguration som tvingar användaren att ange en `-InstanceName`, `-ServiceName`, och för att kontrollera den `-State` parametern.</span><span class="sxs-lookup"><span data-stu-id="4f4a6-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="4f4a6-150">Se även</span><span class="sxs-lookup"><span data-stu-id="4f4a6-150">See also</span></span>

- [<span data-ttu-id="4f4a6-151">Skriva hjälp för DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4f4a6-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="4f4a6-152">Dynamiska konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4f4a6-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="4f4a6-153">Använd konfigurationsdata i dina konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4f4a6-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="4f4a6-154">Separata konfigurations- och miljödata</span><span class="sxs-lookup"><span data-stu-id="4f4a6-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
