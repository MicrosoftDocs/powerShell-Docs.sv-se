---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForSome resurs
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059464"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="f4874-103">DSC WaitForSome resurs</span><span class="sxs-lookup"><span data-stu-id="f4874-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="f4874-104">Gäller för: Windows PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="f4874-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="f4874-105">Den **WaitForSome** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](../../../configurations/configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="f4874-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="f4874-106">Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn**  egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f4874-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="f4874-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4874-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f4874-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f4874-108">Properties</span></span>

|  <span data-ttu-id="f4874-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f4874-109">Property</span></span>  |  <span data-ttu-id="f4874-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f4874-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="f4874-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="f4874-111">NodeCount</span></span>| <span data-ttu-id="f4874-112">Minsta antalet noder som måste vara i önskat läge för den här resursen ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="f4874-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="f4874-113">Nodnamn</span><span class="sxs-lookup"><span data-stu-id="f4874-113">NodeName</span></span>| <span data-ttu-id="f4874-114">Målnoder resursens förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="f4874-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="f4874-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="f4874-115">ResourceName</span></span>| <span data-ttu-id="f4874-116">Resursnamnet förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="f4874-116">The resource name to depend on.</span></span> <span data-ttu-id="f4874-117">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="f4874-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="f4874-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f4874-118">RetryIntervalSec</span></span>| <span data-ttu-id="f4874-119">Antal sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="f4874-119">The number of seconds before retrying.</span></span> <span data-ttu-id="f4874-120">Minimum är 1.</span><span class="sxs-lookup"><span data-stu-id="f4874-120">Minimum is 1.</span></span>|
| <span data-ttu-id="f4874-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="f4874-121">RetryCount</span></span>| <span data-ttu-id="f4874-122">Det maximala antalet gånger att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="f4874-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="f4874-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f4874-123">ThrottleLimit</span></span>| <span data-ttu-id="f4874-124">Antal datorer kan ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="f4874-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="f4874-125">Standardvärdet är standard för nya-cimsession.</span><span class="sxs-lookup"><span data-stu-id="f4874-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="f4874-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f4874-126">DependsOn</span></span> | <span data-ttu-id="f4874-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="f4874-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f4874-128">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f4874-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f4874-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f4874-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="f4874-130">Se [med hjälp av DSC med autentiseringsuppgifterna för användaren](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="f4874-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="f4874-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="f4874-131">Example</span></span>

<span data-ttu-id="f4874-132">Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="f4874-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
