---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForSome resurs
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="f3211-103">DSC WaitForSome resurs</span><span class="sxs-lookup"><span data-stu-id="f3211-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="f3211-104">Gäller för: Windows PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="f3211-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="f3211-105">Den **WaitForAny** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="f3211-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="f3211-106">Den här resursen lyckas om resursen som anges av den **ResourceName** egenskapen finns i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn**  egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f3211-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="f3211-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3211-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f3211-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f3211-108">Properties</span></span>

|  <span data-ttu-id="f3211-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f3211-109">Property</span></span>  |  <span data-ttu-id="f3211-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f3211-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f3211-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="f3211-111">NodeCount</span></span>| <span data-ttu-id="f3211-112">Minsta antal noder som måste finnas i tillståndet för den här resursen ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="f3211-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="f3211-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="f3211-113">NodeName</span></span>| <span data-ttu-id="f3211-114">Målnoder av resursen ska beroende.</span><span class="sxs-lookup"><span data-stu-id="f3211-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="f3211-115">resourceName</span><span class="sxs-lookup"><span data-stu-id="f3211-115">ResourceName</span></span>| <span data-ttu-id="f3211-116">Resursnamnet beroende.</span><span class="sxs-lookup"><span data-stu-id="f3211-116">The resource name to depend on.</span></span>| 
| <span data-ttu-id="f3211-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f3211-117">RetryIntervalSec</span></span>| <span data-ttu-id="f3211-118">Antalet sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="f3211-118">The number of seconds before retrying.</span></span> <span data-ttu-id="f3211-119">Minsta är 1.</span><span class="sxs-lookup"><span data-stu-id="f3211-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="f3211-120">retryCount</span><span class="sxs-lookup"><span data-stu-id="f3211-120">RetryCount</span></span>| <span data-ttu-id="f3211-121">Maximalt antal nya försök.</span><span class="sxs-lookup"><span data-stu-id="f3211-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="f3211-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f3211-122">ThrottleLimit</span></span>| <span data-ttu-id="f3211-123">Antal datorer ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="f3211-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="f3211-124">Standardvärdet är standard för nya cimsession.</span><span class="sxs-lookup"><span data-stu-id="f3211-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="f3211-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f3211-125">DependsOn</span></span> | <span data-ttu-id="f3211-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="f3211-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f3211-127">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f3211-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f3211-128">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f3211-128">PsDscRunAsCredential</span></span> | <span data-ttu-id="f3211-129">Se [använder DSC med autentiseringsuppgifterna för användaren](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="f3211-129">See [Using DSC with User Credentials](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="f3211-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="f3211-130">Example</span></span>

<span data-ttu-id="f3211-131">Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="f3211-131">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

