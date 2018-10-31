---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAny resurs
ms.openlocfilehash: 39100f0fc52092c54bbecab55e3ef3dfabb4c70e
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226057"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="6da57-103">DSC WaitForAny resurs</span><span class="sxs-lookup"><span data-stu-id="6da57-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="6da57-104">Gäller för: Windows PowerShell 5.1 och senare</span><span class="sxs-lookup"><span data-stu-id="6da57-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="6da57-105">Den **WaitForSome** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="6da57-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="6da57-106">Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är med önskat tillstånd på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6da57-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="6da57-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6da57-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="6da57-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6da57-108">Properties</span></span>

|  <span data-ttu-id="6da57-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6da57-109">Property</span></span>  |  <span data-ttu-id="6da57-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6da57-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="6da57-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="6da57-111">ResourceName</span></span>| <span data-ttu-id="6da57-112">Resursnamnet förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="6da57-112">The resource name to depend on.</span></span> <span data-ttu-id="6da57-113">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="6da57-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="6da57-114">Nodnamn</span><span class="sxs-lookup"><span data-stu-id="6da57-114">NodeName</span></span>| <span data-ttu-id="6da57-115">Målnoder resursens förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="6da57-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="6da57-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6da57-116">RetryIntervalSec</span></span>| <span data-ttu-id="6da57-117">Antal sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="6da57-117">The number of seconds before retrying.</span></span> <span data-ttu-id="6da57-118">Minimum är 1.</span><span class="sxs-lookup"><span data-stu-id="6da57-118">Minimum is 1.</span></span>|
| <span data-ttu-id="6da57-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="6da57-119">RetryCount</span></span>| <span data-ttu-id="6da57-120">Det maximala antalet gånger att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="6da57-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="6da57-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6da57-121">ThrottleLimit</span></span>| <span data-ttu-id="6da57-122">Antal datorer kan ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="6da57-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6da57-123">Standardvärdet är standard för nya-cimsession.</span><span class="sxs-lookup"><span data-stu-id="6da57-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="6da57-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6da57-124">DependsOn</span></span> | <span data-ttu-id="6da57-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="6da57-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6da57-126">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6da57-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="6da57-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="6da57-127">Example</span></span>

<span data-ttu-id="6da57-128">Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6da57-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>