---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WaitForSome resurs
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726764"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="88d22-103">DSC WaitForSome resurs</span><span class="sxs-lookup"><span data-stu-id="88d22-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="88d22-104">Gäller för: Windows PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="88d22-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="88d22-105">Den **WaitForSome** Desired State Configuration (DSC) resursen kan användas i ett nod-block i en [DSC-konfiguration](../../../configurations/configurations.md) ange beroenden på konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="88d22-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="88d22-106">Den här resursen lyckas om resursen har angetts av den **ResourceName** egenskapen är i ett minsta antal noder önskade tillstånd (anges av **NodeCount**) definieras av den **nodnamn**  egenskapen.</span><span class="sxs-lookup"><span data-stu-id="88d22-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="88d22-107">**WaitForSome** resource använder Windows Remote Management för att kontrollera tillståndet hos andra noder.</span><span class="sxs-lookup"><span data-stu-id="88d22-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="88d22-108">Läs mer om port och säkerhetskrav för WinRM [säkerhetsöverväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="88d22-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="88d22-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="88d22-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="88d22-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="88d22-110">Properties</span></span>

|  <span data-ttu-id="88d22-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="88d22-111">Property</span></span>  |  <span data-ttu-id="88d22-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88d22-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="88d22-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="88d22-113">NodeCount</span></span>| <span data-ttu-id="88d22-114">Minsta antalet noder som måste vara i önskat läge för den här resursen ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="88d22-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="88d22-115">Nodnamn</span><span class="sxs-lookup"><span data-stu-id="88d22-115">NodeName</span></span>| <span data-ttu-id="88d22-116">Målnoder resursens förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="88d22-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="88d22-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="88d22-117">ResourceName</span></span>| <span data-ttu-id="88d22-118">Resursnamnet förlita sig på.</span><span class="sxs-lookup"><span data-stu-id="88d22-118">The resource name to depend on.</span></span> <span data-ttu-id="88d22-119">Om den här resursen tillhör en annan konfiguration, formatera namn som ”[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] ”</span><span class="sxs-lookup"><span data-stu-id="88d22-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="88d22-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="88d22-120">RetryIntervalSec</span></span>| <span data-ttu-id="88d22-121">Antal sekunder innan du försöker igen.</span><span class="sxs-lookup"><span data-stu-id="88d22-121">The number of seconds before retrying.</span></span> <span data-ttu-id="88d22-122">Minimum är 1.</span><span class="sxs-lookup"><span data-stu-id="88d22-122">Minimum is 1.</span></span>|
| <span data-ttu-id="88d22-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="88d22-123">RetryCount</span></span>| <span data-ttu-id="88d22-124">Det maximala antalet gånger att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="88d22-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="88d22-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="88d22-125">ThrottleLimit</span></span>| <span data-ttu-id="88d22-126">Antal datorer kan ansluta samtidigt.</span><span class="sxs-lookup"><span data-stu-id="88d22-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="88d22-127">Standardvärdet är standard för nya-cimsession.</span><span class="sxs-lookup"><span data-stu-id="88d22-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="88d22-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="88d22-128">DependsOn</span></span> | <span data-ttu-id="88d22-129">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="88d22-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="88d22-130">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="88d22-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="88d22-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="88d22-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="88d22-132">Se [med hjälp av DSC med autentiseringsuppgifterna för användaren](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="88d22-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="88d22-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="88d22-133">Example</span></span>

<span data-ttu-id="88d22-134">Ett exempel på hur du använder den här resursen finns i [att ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="88d22-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
