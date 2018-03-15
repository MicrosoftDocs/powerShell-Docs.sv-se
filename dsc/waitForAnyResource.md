---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAny resurs
ms.openlocfilehash: 43922dbcccb6d06d7d9edfcf16ce4eb107e9d4e6
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="6cac8-103">DSC WaitForAny resurs</span><span class="sxs-lookup"><span data-stu-id="6cac8-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="6cac8-104">Gäller för: Windows PowerShell 5.1 och senare</span><span class="sxs-lookup"><span data-stu-id="6cac8-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="6cac8-105">Den **WaitForSome** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="6cac8-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="6cac8-106">Den här resursen lyckas om om resursen som anges av den **ResourceName** egenskapen finns i tillståndet på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6cac8-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="6cac8-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6cac8-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6cac8-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6cac8-108">Properties</span></span>

|  <span data-ttu-id="6cac8-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6cac8-109">Property</span></span>  |  <span data-ttu-id="6cac8-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6cac8-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="6cac8-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="6cac8-111">ResourceName</span></span>| <span data-ttu-id="6cac8-112">Resursnamnet beroende.</span><span class="sxs-lookup"><span data-stu-id="6cac8-112">The resource name to depend on.</span></span> <span data-ttu-id="6cac8-113">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="6cac8-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="6cac8-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="6cac8-114">NodeName</span></span>| <span data-ttu-id="6cac8-115">Målnoder av resursen ska beroende.</span><span class="sxs-lookup"><span data-stu-id="6cac8-115">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="6cac8-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6cac8-116">RetryIntervalSec</span></span>| <span data-ttu-id="6cac8-117">Antalet sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="6cac8-117">The number of seconds before retrying.</span></span> <span data-ttu-id="6cac8-118">Minsta är 1.</span><span class="sxs-lookup"><span data-stu-id="6cac8-118">Minimum is 1.</span></span>| 
| <span data-ttu-id="6cac8-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="6cac8-119">RetryCount</span></span>| <span data-ttu-id="6cac8-120">Maximalt antal nya försök.</span><span class="sxs-lookup"><span data-stu-id="6cac8-120">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="6cac8-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6cac8-121">ThrottleLimit</span></span>| <span data-ttu-id="6cac8-122">Antal datorer ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="6cac8-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6cac8-123">Standardvärdet är standard för nya cimsession.</span><span class="sxs-lookup"><span data-stu-id="6cac8-123">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="6cac8-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="6cac8-124">DependsOn</span></span> | <span data-ttu-id="6cac8-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="6cac8-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6cac8-126">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6cac8-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="6cac8-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="6cac8-127">Example</span></span>

<span data-ttu-id="6cac8-128">Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6cac8-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

