---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WaitForAll-resurs
description: DSC WaitForAll-resurs
ms.openlocfilehash: a477584cf97a56815bda9973cb2befc9b71d14d1
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143117"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="7c9c3-103">DSC WaitForAll-resurs</span><span class="sxs-lookup"><span data-stu-id="7c9c3-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="7c9c3-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="7c9c3-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7c9c3-105">Du kan använda den **WAITFORALL** DSC-resursen (Desired State Configuration) i ett Node-block i en [DSC-konfiguration](../../../configurations/configurations.md) för att ange beroenden för konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

<span data-ttu-id="7c9c3-106">Den här resursen slutförs om resursen som anges av egenskapen **resourceName** har önskat tillstånd på alla målnod som definierats i egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="7c9c3-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="7c9c3-107">**WaitForAll** -resursen använder Windows Remote Management för att kontrol lera status för andra noder.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="7c9c3-108">Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="7c9c3-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="syntax"></a><span data-ttu-id="7c9c3-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="7c9c3-109">Syntax</span></span>

```Syntax
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7c9c3-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7c9c3-110">Properties</span></span>

|<span data-ttu-id="7c9c3-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7c9c3-111">Property</span></span> |<span data-ttu-id="7c9c3-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7c9c3-112">Description</span></span> |
|---|---|
|<span data-ttu-id="7c9c3-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="7c9c3-113">ResourceName</span></span> |<span data-ttu-id="7c9c3-114">Resurs namnet som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-114">The resource name to depend on.</span></span> <span data-ttu-id="7c9c3-115">Om den här resursen tillhör en annan konfiguration formaterar du namnet som `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]` .</span><span class="sxs-lookup"><span data-stu-id="7c9c3-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="7c9c3-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="7c9c3-116">NodeName</span></span> |<span data-ttu-id="7c9c3-117">Målvärdena för resursen som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="7c9c3-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="7c9c3-118">RetryIntervalSec</span></span> |<span data-ttu-id="7c9c3-119">Antalet sekunder innan nytt försök.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-119">The number of seconds before retrying.</span></span> <span data-ttu-id="7c9c3-120">Minimivärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-120">Minimum is 1.</span></span> |
|<span data-ttu-id="7c9c3-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="7c9c3-121">RetryCount</span></span> |<span data-ttu-id="7c9c3-122">Det maximala antalet försök att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="7c9c3-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7c9c3-123">ThrottleLimit</span></span> |<span data-ttu-id="7c9c3-124">Antal datorer som ska anslutas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="7c9c3-125">Standardvärdet är `New-CimSession` standard.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7c9c3-126">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7c9c3-126">Common properties</span></span>

|<span data-ttu-id="7c9c3-127">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7c9c3-127">Property</span></span> |<span data-ttu-id="7c9c3-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7c9c3-128">Description</span></span> |
|---|---|
|<span data-ttu-id="7c9c3-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7c9c3-129">DependsOn</span></span> |<span data-ttu-id="7c9c3-130">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7c9c3-131">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="7c9c3-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7c9c3-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7c9c3-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="7c9c3-133">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7c9c3-134">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7c9c3-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7c9c3-135">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7c9c3-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c9c3-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="7c9c3-136">Example</span></span>

<span data-ttu-id="7c9c3-137">Ett exempel på hur du använder den här resursen finns i [ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="7c9c3-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
