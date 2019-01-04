---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 02e1b9856942cf28e77d83dac89681a08cf6bb74
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012457"
---
# <a name="dsc-resources"></a><span data-ttu-id="7bc60-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="7bc60-103">DSC Resources</span></span>

><span data-ttu-id="7bc60-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7bc60-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7bc60-105">Desired State Configuration (DSC) resurser innehåller byggstenarna för en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="7bc60-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="7bc60-106">En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som lokala Configuration Manager (LCM)-anrop till ”gör den det”.</span><span class="sxs-lookup"><span data-stu-id="7bc60-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="7bc60-107">En resurs kan utforma något som allmän som en fil eller så specifik som en inställning för IIS-server.</span><span class="sxs-lookup"><span data-stu-id="7bc60-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="7bc60-108">Grupper av som resurser kombineras till en DSC-modul som organiserar alla filerna som krävs i att en struktur som är portabelt och innehåller metadata för att identifiera hur resurserna är avsedda att användas i.</span><span class="sxs-lookup"><span data-stu-id="7bc60-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="7bc60-109">Varje resurs har en \* schema som anger den syntax som krävs för att använda resursen i en [Configuration](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="7bc60-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="7bc60-110">Schemat för en resurs kan definieras på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="7bc60-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="7bc60-111">**'Schema.Mof'** fil: De flesta resurser definiera sina *schemat* i en schema.mof fil, använda [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="7bc60-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="7bc60-112">**”\<Resursnamn\>. schema.psm1'** fil: [Sammansatta resurser](../configurations/compositeConfigs.md) definiera sina *schemat* i en ”<ResourceName>. schema.psm1-fil med hjälp av en [Parameterblocket](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="7bc60-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="7bc60-113">**”\<Resursnamn\>.psm1'** fil: Klassen baserat DSC-resurser definiera sina *schemat* i klassdefinitionen.</span><span class="sxs-lookup"><span data-stu-id="7bc60-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="7bc60-114">Syntax objekt betecknas som klassegenskaper.</span><span class="sxs-lookup"><span data-stu-id="7bc60-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="7bc60-115">Mer information finns i [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="7bc60-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="7bc60-116">Använd för att hämta syntaxen för en DSC-resurs i [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet med den `-Syntax` parametern.</span><span class="sxs-lookup"><span data-stu-id="7bc60-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="7bc60-117">Den här användningen är ungefär som att använda [Get-Command](/powershell/module/microsoft.powershell.core/get-command) med den `-Syntax` parametern för att hämta cmdlet-syntax.</span><span class="sxs-lookup"><span data-stu-id="7bc60-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="7bc60-118">Du ser utdata visar den mall som användes för en resurs-block för den resurs som du anger.</span><span class="sxs-lookup"><span data-stu-id="7bc60-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="7bc60-119">Du ser utdata bör likna utdata nedan, även om den här resursen syntax kan ändras i framtiden.</span><span class="sxs-lookup"><span data-stu-id="7bc60-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="7bc60-120">Som cmdlet-syntax i *nycklar* visas inom hakparentes är valfria.</span><span class="sxs-lookup"><span data-stu-id="7bc60-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="7bc60-121">Typerna ange vilken typ av data som förväntar sig att varje nyckel.</span><span class="sxs-lookup"><span data-stu-id="7bc60-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc60-122">Den **Kontrollera** nyckeln är valfri eftersom standard ”aktuella”.</span><span class="sxs-lookup"><span data-stu-id="7bc60-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="7bc60-123">I en konfiguration för en **Service** resource block kan se ut så här för att **Kontrollera** som tjänsten Spooler körs.</span><span class="sxs-lookup"><span data-stu-id="7bc60-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc60-124">Innan du använder en resurs i en konfiguration, måste du importera den med hjälp av [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="7bc60-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="7bc60-125">Konfigurationer kan innehålla flera instanser av samma resurstypen.</span><span class="sxs-lookup"><span data-stu-id="7bc60-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="7bc60-126">Varje instans måste vara unika namn.</span><span class="sxs-lookup"><span data-stu-id="7bc60-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="7bc60-127">I följande exempel visas en andra **Service** resource block har lagts till för att konfigurera tjänsten ”DHCP”.</span><span class="sxs-lookup"><span data-stu-id="7bc60-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="7bc60-128">Från och med PowerShell 5.0, intellisense lades till för DSC.</span><span class="sxs-lookup"><span data-stu-id="7bc60-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="7bc60-129">Den här nya funktionen kan du använda \<FLIKEN\> och \<Ctrl + blanksteg\> till automatisk komplettering nyckelnamn.</span><span class="sxs-lookup"><span data-stu-id="7bc60-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Tabbifyllning för resursen](../media/resource-tabcompletion.png)
