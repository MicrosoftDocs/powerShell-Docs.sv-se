---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForSome resurs
ms.openlocfilehash: 8b0ad0dbd31816cc673c7f77945927987e90e08b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="f2c66-103">DSC WaitForSome resurs</span><span class="sxs-lookup"><span data-stu-id="f2c66-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="f2c66-104">Gäller för: Windows PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="f2c66-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="f2c66-105">Den **WaitForAny** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="f2c66-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="f2c66-106">Den här resursen lyckas om resursen som anges av den **ResourceName** egenskapen finns i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn**  egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f2c66-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="f2c66-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2c66-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="f2c66-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f2c66-108">Properties</span></span>

|  <span data-ttu-id="f2c66-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f2c66-109">Property</span></span>  |  <span data-ttu-id="f2c66-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2c66-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f2c66-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="f2c66-111">NodeCount</span></span>| <span data-ttu-id="f2c66-112">Minsta antal noder som måste finnas i tillståndet för den här resursen ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="f2c66-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="f2c66-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="f2c66-113">NodeName</span></span>| <span data-ttu-id="f2c66-114">Målnoder av resursen ska beroende.</span><span class="sxs-lookup"><span data-stu-id="f2c66-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="f2c66-115">resourceName</span><span class="sxs-lookup"><span data-stu-id="f2c66-115">ResourceName</span></span>| <span data-ttu-id="f2c66-116">Resursnamnet beroende.</span><span class="sxs-lookup"><span data-stu-id="f2c66-116">The resource name to depend on.</span></span> <span data-ttu-id="f2c66-117">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="f2c66-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="f2c66-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f2c66-118">RetryIntervalSec</span></span>| <span data-ttu-id="f2c66-119">Antalet sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="f2c66-119">The number of seconds before retrying.</span></span> <span data-ttu-id="f2c66-120">Minsta är 1.</span><span class="sxs-lookup"><span data-stu-id="f2c66-120">Minimum is 1.</span></span>| 
| <span data-ttu-id="f2c66-121">retryCount</span><span class="sxs-lookup"><span data-stu-id="f2c66-121">RetryCount</span></span>| <span data-ttu-id="f2c66-122">Maximalt antal nya försök.</span><span class="sxs-lookup"><span data-stu-id="f2c66-122">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="f2c66-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f2c66-123">ThrottleLimit</span></span>| <span data-ttu-id="f2c66-124">Antal datorer ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="f2c66-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="f2c66-125">Standardvärdet är standard för nya cimsession.</span><span class="sxs-lookup"><span data-stu-id="f2c66-125">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="f2c66-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f2c66-126">DependsOn</span></span> | <span data-ttu-id="f2c66-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="f2c66-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f2c66-128">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f2c66-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f2c66-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f2c66-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="f2c66-130">Se [använder DSC med autentiseringsuppgifterna för användaren](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="f2c66-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="f2c66-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="f2c66-131">Example</span></span>

<span data-ttu-id="f2c66-132">Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="f2c66-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

