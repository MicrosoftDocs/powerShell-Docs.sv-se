---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAll resurs
ms.openlocfilehash: 2054d2af7cd7dd839c62e77c1d4b6eee5cff34ab
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="5fb84-103">DSC WaitForAll resurs</span><span class="sxs-lookup"><span data-stu-id="5fb84-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="5fb84-104">Gäller för: Windows PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="5fb84-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="5fb84-105">Den **WaitForAll** önskade tillstånd Configuration DSC ()-resursen kan användas i ett nod-block i en [DSC-konfigurationen](configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="5fb84-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="5fb84-106">Den här resursen lyckas om om resursen som anges av den **ResourceName** egenskapen finns i tillståndet på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5fb84-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="5fb84-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5fb84-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="5fb84-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="5fb84-108">Properties</span></span>

|  <span data-ttu-id="5fb84-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="5fb84-109">Property</span></span>  |  <span data-ttu-id="5fb84-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5fb84-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="5fb84-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="5fb84-111">ResourceName</span></span>| <span data-ttu-id="5fb84-112">Resursnamnet beroende.</span><span class="sxs-lookup"><span data-stu-id="5fb84-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="5fb84-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="5fb84-113">NodeName</span></span>| <span data-ttu-id="5fb84-114">Målnoder av resursen ska beroende.</span><span class="sxs-lookup"><span data-stu-id="5fb84-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="5fb84-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="5fb84-115">RetryIntervalSec</span></span>| <span data-ttu-id="5fb84-116">Antalet sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="5fb84-116">The number of seconds before retrying.</span></span> <span data-ttu-id="5fb84-117">Minsta är 1.</span><span class="sxs-lookup"><span data-stu-id="5fb84-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="5fb84-118">retryCount</span><span class="sxs-lookup"><span data-stu-id="5fb84-118">RetryCount</span></span>| <span data-ttu-id="5fb84-119">Maximalt antal nya försök.</span><span class="sxs-lookup"><span data-stu-id="5fb84-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="5fb84-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5fb84-120">ThrottleLimit</span></span>| <span data-ttu-id="5fb84-121">Antal datorer ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="5fb84-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="5fb84-122">Standardvärdet är standard för nya cimsession.</span><span class="sxs-lookup"><span data-stu-id="5fb84-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="5fb84-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5fb84-123">DependsOn</span></span> | <span data-ttu-id="5fb84-124">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="5fb84-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5fb84-125">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5fb84-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="5fb84-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="5fb84-126">Example</span></span>

<span data-ttu-id="5fb84-127">Ett exempel på hur du använder den här resursen finns [angett beroenden mellan noder](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="5fb84-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

