---
ms.date: 07/16/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsFeatureSet-resurs
ms.openlocfilehash: 856c56e0b35a26add729ef77db9dca71fdc0a4d0
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463864"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="2b199-103">DSC WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="2b199-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="2b199-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="2b199-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="2b199-105">**WindowsFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att se till att roller och funktioner läggs till eller tas bort på en målnod.</span><span class="sxs-lookup"><span data-stu-id="2b199-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="2b199-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsFeature-resursen](windowsfeatureResource.md) för varje funktion som anges i egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="2b199-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="2b199-107">Använd den här resursen när du vill konfigurera ett antal Windows-funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="2b199-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b199-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b199-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2b199-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2b199-109">Properties</span></span>

|  <span data-ttu-id="2b199-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2b199-110">Property</span></span>  |  <span data-ttu-id="2b199-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2b199-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="2b199-112">Name</span><span class="sxs-lookup"><span data-stu-id="2b199-112">Name</span></span> |<span data-ttu-id="2b199-113">Namnen på de roller eller funktioner som du vill se läggs till eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="2b199-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="2b199-114">Detta är samma som egenskapen **Name** för cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) och inte visnings namnet för rollerna eller funktionerna.</span><span class="sxs-lookup"><span data-stu-id="2b199-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="2b199-115">Källa</span><span class="sxs-lookup"><span data-stu-id="2b199-115">Source</span></span> |<span data-ttu-id="2b199-116">Anger platsen för den käll fil som ska användas för installation, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="2b199-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="2b199-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="2b199-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="2b199-118">Ange den här egenskapen till `$true` att inkludera alla nödvändiga underfunktioner med de funktioner som du anger med egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="2b199-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="2b199-119">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="2b199-119">Credential</span></span> |<span data-ttu-id="2b199-120">De autentiseringsuppgifter som ska användas för att lägga till eller ta bort roller och funktioner.</span><span class="sxs-lookup"><span data-stu-id="2b199-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="2b199-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="2b199-121">LogPath</span></span> |<span data-ttu-id="2b199-122">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2b199-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2b199-123">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="2b199-123">Common properties</span></span>

|<span data-ttu-id="2b199-124">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2b199-124">Property</span></span> |<span data-ttu-id="2b199-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2b199-125">Description</span></span> |
|---|---|
|<span data-ttu-id="2b199-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2b199-126">DependsOn</span></span> |<span data-ttu-id="2b199-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="2b199-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2b199-128">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="2b199-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2b199-129">Kontrol</span><span class="sxs-lookup"><span data-stu-id="2b199-129">Ensure</span></span> |<span data-ttu-id="2b199-130">Anger om roller eller funktioner läggs till.</span><span class="sxs-lookup"><span data-stu-id="2b199-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="2b199-131">Om du vill kontrol lera att rollerna eller funktionerna har lagts till ställer du in den här egenskapen som **tillgänglig**.</span><span class="sxs-lookup"><span data-stu-id="2b199-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="2b199-132">För att säkerställa att rollerna eller funktionerna tas bort ställer du in egenskapen på **saknas**.</span><span class="sxs-lookup"><span data-stu-id="2b199-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="2b199-133">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="2b199-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="2b199-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2b199-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="2b199-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="2b199-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="2b199-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="2b199-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="2b199-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="2b199-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="2b199-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="2b199-138">Example</span></span>

<span data-ttu-id="2b199-139">Följande konfiguration säkerställer att funktionerna för **webb server** (IIS) och **SMTP-servern** och alla underfunktioner i respektive är installerade.</span><span class="sxs-lookup"><span data-stu-id="2b199-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
