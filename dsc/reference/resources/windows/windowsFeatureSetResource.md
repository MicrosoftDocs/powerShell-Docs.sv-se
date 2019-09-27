---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsFeatureSet-resurs
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323925"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="117e5-103">DSC WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="117e5-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="117e5-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="117e5-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="117e5-105">**WindowsFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att se till att roller och funktioner läggs till eller tas bort på en målnod.</span><span class="sxs-lookup"><span data-stu-id="117e5-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="117e5-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsFeature-resursen](windowsfeatureResource.md) för varje funktion som anges i egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="117e5-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="117e5-107">Använd den här resursen när du vill konfigurera ett antal Windows-funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="117e5-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="117e5-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="117e5-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="117e5-109">properties</span><span class="sxs-lookup"><span data-stu-id="117e5-109">Properties</span></span>

|  <span data-ttu-id="117e5-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="117e5-110">Property</span></span>  |  <span data-ttu-id="117e5-111">Description</span><span class="sxs-lookup"><span data-stu-id="117e5-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="117e5-112">Name</span><span class="sxs-lookup"><span data-stu-id="117e5-112">Name</span></span> |<span data-ttu-id="117e5-113">Namnen på de roller eller funktioner som du vill se läggs till eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="117e5-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="117e5-114">Detta är samma som egenskapen **Name** för cmdleten [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) och inte visnings namnet för rollerna eller funktionerna.</span><span class="sxs-lookup"><span data-stu-id="117e5-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="117e5-115">Source</span><span class="sxs-lookup"><span data-stu-id="117e5-115">Source</span></span> |<span data-ttu-id="117e5-116">Anger platsen för den käll fil som ska användas för installation, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="117e5-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="117e5-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="117e5-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="117e5-118">Ange den här egenskapen `$true` till att inkludera alla nödvändiga underfunktioner med de funktioner som du anger med egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="117e5-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="117e5-119">Certifiering</span><span class="sxs-lookup"><span data-stu-id="117e5-119">Credential</span></span> |<span data-ttu-id="117e5-120">De autentiseringsuppgifter som ska användas för att lägga till eller ta bort roller och funktioner.</span><span class="sxs-lookup"><span data-stu-id="117e5-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="117e5-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="117e5-121">LogPath</span></span> |<span data-ttu-id="117e5-122">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="117e5-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="117e5-123">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="117e5-123">Common properties</span></span>

|<span data-ttu-id="117e5-124">Egenskap</span><span class="sxs-lookup"><span data-stu-id="117e5-124">Property</span></span> |<span data-ttu-id="117e5-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="117e5-125">Description</span></span> |
|---|---|
|<span data-ttu-id="117e5-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="117e5-126">DependsOn</span></span> |<span data-ttu-id="117e5-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="117e5-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="117e5-128">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="117e5-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="117e5-129">Kontrol</span><span class="sxs-lookup"><span data-stu-id="117e5-129">Ensure</span></span> |<span data-ttu-id="117e5-130">Anger om roller eller funktioner läggs till.</span><span class="sxs-lookup"><span data-stu-id="117e5-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="117e5-131">Om du vill kontrol lera att rollerna eller funktionerna har lagts till ställer du in den här egenskapen som **tillgänglig**.</span><span class="sxs-lookup"><span data-stu-id="117e5-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="117e5-132">För att säkerställa att rollerna eller funktionerna tas bort ställer du in egenskapen på **saknas**.</span><span class="sxs-lookup"><span data-stu-id="117e5-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="117e5-133">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="117e5-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="117e5-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="117e5-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="117e5-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="117e5-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="117e5-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="117e5-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="117e5-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="117e5-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="117e5-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="117e5-138">Example</span></span>

<span data-ttu-id="117e5-139">Följande konfiguration säkerställer att funktionerna för **webb server** (IIS) och **SMTP-servern** och alla underfunktioner i respektive är installerade.</span><span class="sxs-lookup"><span data-stu-id="117e5-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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