---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForAll resurs
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726875"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="a84b1-103">DSC WaitForAll resurs</span><span class="sxs-lookup"><span data-stu-id="a84b1-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="a84b1-104">Gäller för: Windows PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="a84b1-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="a84b1-105">Den **WaitForAll** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](../../../configurations/configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="a84b1-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a84b1-106">Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är med önskat tillstånd på alla målnoder som definierats i den **nodnamn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a84b1-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="a84b1-107">**WaitForAll** resource använder Windows Remote Management för att kontrollera tillståndet hos andra noder.</span><span class="sxs-lookup"><span data-stu-id="a84b1-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="a84b1-108">Läs mer om port och säkerhetskrav för WinRM [säkerhetsöverväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="a84b1-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="a84b1-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="a84b1-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a84b1-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="a84b1-110">Properties</span></span>

|  <span data-ttu-id="a84b1-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="a84b1-111">Property</span></span>  |  <span data-ttu-id="a84b1-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a84b1-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="a84b1-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="a84b1-113">ResourceName</span></span>| <span data-ttu-id="a84b1-114">Resursnamnet förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="a84b1-114">The resource name to depend on.</span></span> <span data-ttu-id="a84b1-115">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="a84b1-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="a84b1-116">Nodnamn</span><span class="sxs-lookup"><span data-stu-id="a84b1-116">NodeName</span></span>| <span data-ttu-id="a84b1-117">Målnoder resursens förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="a84b1-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="a84b1-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a84b1-118">RetryIntervalSec</span></span>| <span data-ttu-id="a84b1-119">Antal sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="a84b1-119">The number of seconds before retrying.</span></span> <span data-ttu-id="a84b1-120">Minimum är 1.</span><span class="sxs-lookup"><span data-stu-id="a84b1-120">Minimum is 1.</span></span>|
| <span data-ttu-id="a84b1-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a84b1-121">RetryCount</span></span>| <span data-ttu-id="a84b1-122">Det maximala antalet gånger att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="a84b1-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="a84b1-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a84b1-123">ThrottleLimit</span></span>| <span data-ttu-id="a84b1-124">Antal datorer kan ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="a84b1-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a84b1-125">Standardvärdet är standard för nya-cimsession.</span><span class="sxs-lookup"><span data-stu-id="a84b1-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="a84b1-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a84b1-126">DependsOn</span></span> | <span data-ttu-id="a84b1-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="a84b1-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a84b1-128">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a84b1-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a84b1-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="a84b1-129">Example</span></span>

<span data-ttu-id="a84b1-130">Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a84b1-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
