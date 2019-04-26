---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAny resurs
ms.openlocfilehash: 55869f665837b422c006f4cfb3e91366fac60362
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076840"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="ec6d3-103">DSC WaitForAny resurs</span><span class="sxs-lookup"><span data-stu-id="ec6d3-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="ec6d3-104">Gäller för: Windows PowerShell 5.1 och senare</span><span class="sxs-lookup"><span data-stu-id="ec6d3-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="ec6d3-105">Den **WaitForAny** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](../../../configurations/configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ec6d3-106">Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är med önskat tillstånd på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="ec6d3-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec6d3-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ec6d3-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="ec6d3-108">Properties</span></span>

|  <span data-ttu-id="ec6d3-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="ec6d3-109">Property</span></span>  |  <span data-ttu-id="ec6d3-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ec6d3-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="ec6d3-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="ec6d3-111">ResourceName</span></span>| <span data-ttu-id="ec6d3-112">Resursnamnet förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-112">The resource name to depend on.</span></span> <span data-ttu-id="ec6d3-113">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="ec6d3-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="ec6d3-114">Nodnamn</span><span class="sxs-lookup"><span data-stu-id="ec6d3-114">NodeName</span></span>| <span data-ttu-id="ec6d3-115">Målnoder resursens förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="ec6d3-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ec6d3-116">RetryIntervalSec</span></span>| <span data-ttu-id="ec6d3-117">Antal sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-117">The number of seconds before retrying.</span></span> <span data-ttu-id="ec6d3-118">Minimum är 1.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-118">Minimum is 1.</span></span>|
| <span data-ttu-id="ec6d3-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ec6d3-119">RetryCount</span></span>| <span data-ttu-id="ec6d3-120">Det maximala antalet gånger att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="ec6d3-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ec6d3-121">ThrottleLimit</span></span>| <span data-ttu-id="ec6d3-122">Antal datorer kan ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ec6d3-123">Standardvärdet är standard för nya-cimsession.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="ec6d3-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ec6d3-124">DependsOn</span></span> | <span data-ttu-id="ec6d3-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ec6d3-126">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ec6d3-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="ec6d3-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="ec6d3-127">Example</span></span>

<span data-ttu-id="ec6d3-128">Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="ec6d3-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
