---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WaitForSome-resurs
description: DSC WaitForSome-resurs
ms.openlocfilehash: bc9c3df2b476e7046ccfe6257acc1d1641e7594b
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143100"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="456d0-103">DSC WaitForSome-resurs</span><span class="sxs-lookup"><span data-stu-id="456d0-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="456d0-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="456d0-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="456d0-105">Du kan använda den **WAITFORSOME** DSC-resursen (Desired State Configuration) i ett Node-block i en [DSC-konfiguration](../../../configurations/configurations.md) för att ange beroenden för konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="456d0-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

<span data-ttu-id="456d0-106">Den här resursen slutförs om resursen som anges av egenskapen **resourceName** har önskat tillstånd på ett minsta antal noder (anges av **NodeCount** ) som definieras av egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="456d0-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount** ) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="456d0-107">**WaitForSome** -resursen använder Windows Remote Management för att kontrol lera status för andra noder.</span><span class="sxs-lookup"><span data-stu-id="456d0-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="456d0-108">Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="456d0-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="syntax"></a><span data-ttu-id="456d0-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="456d0-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="456d0-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="456d0-110">Properties</span></span>

|<span data-ttu-id="456d0-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="456d0-111">Property</span></span> |<span data-ttu-id="456d0-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="456d0-112">Description</span></span> |
|---|---|
|<span data-ttu-id="456d0-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="456d0-113">NodeCount</span></span> |<span data-ttu-id="456d0-114">Det minsta antalet noder som måste ha önskat tillstånd för att resursen ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="456d0-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="456d0-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="456d0-115">NodeName</span></span> |<span data-ttu-id="456d0-116">Målvärdena för resursen som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="456d0-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="456d0-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="456d0-117">ResourceName</span></span> |<span data-ttu-id="456d0-118">Resurs namnet som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="456d0-118">The resource name to depend on.</span></span> <span data-ttu-id="456d0-119">Om den här resursen tillhör en annan konfiguration formaterar du namnet som `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]` .</span><span class="sxs-lookup"><span data-stu-id="456d0-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="456d0-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="456d0-120">RetryIntervalSec</span></span> |<span data-ttu-id="456d0-121">Antalet sekunder innan nytt försök.</span><span class="sxs-lookup"><span data-stu-id="456d0-121">The number of seconds before retrying.</span></span> <span data-ttu-id="456d0-122">Minimivärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="456d0-122">Minimum is 1.</span></span> |
|<span data-ttu-id="456d0-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="456d0-123">RetryCount</span></span> |<span data-ttu-id="456d0-124">Det maximala antalet försök att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="456d0-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="456d0-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="456d0-125">ThrottleLimit</span></span> |<span data-ttu-id="456d0-126">Antal datorer som ska anslutas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="456d0-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="456d0-127">Standardvärdet är `New-CimSession` standard.</span><span class="sxs-lookup"><span data-stu-id="456d0-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="456d0-128">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="456d0-128">Common properties</span></span>

|<span data-ttu-id="456d0-129">Egenskap</span><span class="sxs-lookup"><span data-stu-id="456d0-129">Property</span></span> |<span data-ttu-id="456d0-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="456d0-130">Description</span></span> |
|---|---|
|<span data-ttu-id="456d0-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="456d0-131">DependsOn</span></span> |<span data-ttu-id="456d0-132">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="456d0-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="456d0-133">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="456d0-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="456d0-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="456d0-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="456d0-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="456d0-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="456d0-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="456d0-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="456d0-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="456d0-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="456d0-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="456d0-138">Example</span></span>

<span data-ttu-id="456d0-139">Ett exempel på hur du använder den här resursen finns i [ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="456d0-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
